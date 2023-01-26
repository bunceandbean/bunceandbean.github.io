---
layout: post
title: "An Introductory FizzBuzz"
comments: true
description: "An Introductory FizzBuzz"
keywords: ""
---

Since the beginning of time (Wikipedia didn't provide a date), FizzBuzz has been used to screen programmers and figure out what their coding style is like. It is unique in this aspect, as it is one of the only common programming puzzles focused more on implementation style than problem solving. Solving FizzBuzz is relatively simple, and any programmer with more than three days of experience can succeed. As a welcome to my first blog post, here is my implementation of FizzBuzz in Python.

### The Beautiful fizzbuzz.py

```python
def fizzbuzz(upper_bound):
  for i in range(1, upper_bound + 1):
    s = ""
    if i % 3 == 0:
      s += "Fizz"
    if i % 5 == 0:
      s += "Buzz"
    if not s:
      s = str(i)
    print(s)
```

#### Cheers!