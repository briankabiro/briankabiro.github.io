---
title: The dark side of Array#include?
layout: article
---

I was recently writing some code in Ruby to check whether a word did **not** include a vowel,that is, checking that it only had consonants.

The code looked something like this.

```ruby
if !word.include? vowel
  ## initiate countdown sequence
end
```

If this was to go through code review, one of the suggestions would be to use `unless` to replace `if !`

I could then write this as:

```ruby
unless word.include? vowel
  ## commence code review!
end
```

I've had problems reading code that uses `unless` because it adds a layer of complexity to understanding.

#### Python's "not in"

I found myself yearning for the `not in` clause from Python which is closer to English.

In Python, I could do:

```python
if vowel not in word:
  # go to mars
end
```

I think that **not in** reads better especially when checking whether an item is inside an array.

Maybe it's time for Ruby to:

```ruby
import "not in" from python;
```