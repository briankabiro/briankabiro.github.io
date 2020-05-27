---
title: The curious case of false.blank?
layout: article
---

I was testing a Rails model to check whether a required field was passed in when a record is being created.

The test looked like this:
```ruby
it { should validate_presence_of(:fired) }
```

and the corresponding code in the model was:

```ruby
validates_presence_of :fired
```

The `:fired` parameter was a boolean value that could either be true or false. All of this looked rosy until I ran the tests.

This specific assertion failed while everything else passed. What a bummer!

I started a wild "bool" chase that took me to the migration files, resetting the database, the Rails console and finally back to the model. I narrowed down the issue to the fact that **fired** was a boolean value.

I tried searching for the issue but I didn't find the answer I was looking for. 

Funny enough when I searched for it recently, I found the answer immediately. I don't know what that says about my search skills but I'm a work in progress.

After failed searching, I decided to go to the Rails codebase to see if I would find the solution there.

I searched for the `validates_presence_of` method in the repo and found the [goose](https://github.com/rails/rails/blob/b2eb1d1c55a59fee1e6c4cba7030d8ceb524267c/activerecord/lib/active_record/validations/presence.rb#L28).

```md
# If you want to validate the presence of a boolean field (where the real values
# are true and false), you will want to use
# <tt>validates_inclusion_of :field_name, in: [true, false]</tt>.

# This is due to the way Object#blank? handles boolean values:
# <tt>false.blank? # => true</tt>.
```

The `validates_presence_of` method raises an error if the value it receives is blank. It checks whether it is blank by calling `.blank?` on it.

In my code, when I passed false as a value, *false.blank?* evaluated to true so the validation failed.

The .blank? method doesn't actually exist in Ruby but ActiveRecord uses it to check falsy values.

Armed with this knowledge, I ran to my editor and made the change to both the model and the test.

```ruby
validates_inclusion_in :fired, in: [true, false]
```

The tests turned green. 

This adventure showed me why it's important to be comfortable digging into the source code of any tool that I use. 

It was built by someone just like me and that the answer might be there in plain sight.
