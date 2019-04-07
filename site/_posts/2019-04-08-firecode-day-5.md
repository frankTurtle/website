---
layout: single
title: 'Day Five'
date: 2019-04-08 18:30:00 -0400
categories: prep interview algorithms firecode
---

# 100 days challenge -- Day Five

Well, so far so good! I've been able to complete Six problems so far. I feel like work and school are getting in the way ;)

## Problem Six
#### Name:
Palindrome Tester

#### Description:
A palindrome is a string or sequence of characters that reads the same backward and forward. For example, "madam" is a palindrome.
Write a function that takes in a ```string``` and returns a ```Boolean -> True``` if the input ```string``` is a palindrome and ```False```
if it is not. An empty string is considered a palindrome. You also need to account for the space character. For example, "race car" should return ```False``` as read backward it is "rac ecar".

#### Example:
```python 
is_palindrome("madam") -> True

is_palindrome("aabb") -> False

is_palindrome("race car") -> False

is_palindrome("") -> True
```

#### Solution:
```python
def is_palindrome(input_string):
    if not input_string:
        return True
    
    return input_string[:] == input_string[::-1]
```

#### Analysis:
You've to love the power of python slicing! After I submitted and checked over the other answers, I realize that the first two lines are not even required. Even better! A single short one line answer -> ```return input_string == input_string[::-1]```

I would say that this would be O(n) for both runtime and space. It seems to be a trend with these level one problems.

