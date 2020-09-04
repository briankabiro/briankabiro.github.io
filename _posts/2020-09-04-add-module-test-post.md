---
title:  A better way to test a module in Ruby
layout: article
---

One way of testing modules in Ruby is initializing the class that includes the module e.g a User model and then calling the methods using the class.

While there is nothing wrong with this, it's overkill and is not a best practice.

A better way would be to create a regular class, include the module and use that class to test that method. Walk with me...

Let's say we have a module named `TaxHelper`.

```ruby
  module TaxHelper
    def calculate_tax
      ## cool tax stuff here
    end
  end
```

In our test setup, we can create a new class and include the methods there.

```ruby
  subject do
    klass = Class.new
    klass.include TaxHelper ## klass.extend if we want class methods
  end
```

Now we can test the module's methods without having to use the main class.

```ruby
  expect(subject.calculate_tax(10)).to eq(tax)
```

And voila, we don't have to load a huge class just to test a few methods.
