---
title: Beware the unless
layout: article
---

I was recently writing some code in Ruby to check whether a word did not include a vowel i.e it only had consonants.

```ruby
If !word.include? vowel
  ## initiate countdown sequence
end
```

If this was to go through code review, one of the suggestions would be to use `unless`.

I could then write this as:

```ruby
unless word.include? vowel
  ## commence code review!
end
```

Unless is easy to write but harder to understand when paired with a complex expression.

#### Python's not in

I found myself yearning for the `not in` clause from Python which is closer to English.

In Python, I could do:

```python
if vowel not in word:
  # launch the rocket
end
```

