---
layout: single
title: 'Day Four'
date: 2019-04-07 07:24:00 -0400
categories: prep interview algorithms firecode
---

# 100 days challenge -- Day Four

Well, so far so good! I've been able to complete five problems so far. I'll drop a little detail about each below

## Problem One
#### Name:
Find One Missing Number from 1 to 10

#### Description:
Given an list containing 9 numbers ranging from 1 to 10, write a function to find the missing number. Assume you have 9 numbers between 1 to 10 and only one number is missing.

#### Example:
```python 
input_list: [1, 2, 4, 5, 6, 7, 8, 9, 10]
find_missing_number(input_list) => 3
```

#### Solution:
```python
def find_missing_number(list_numbers):
    for num in range(1, 10):
        if num not in list_numbers:
            return num
```

#### Analysis:
I felt that this one was pretty straightforward. Given the bounds of only having a list of numbers form 1 to 10 made it even easier. I could've written the function to be more generic though. 

I would say that this would be O(n) for both runtime and space. I only hesitate because I'm not positive if the ``` if num not in list_numbers ``` part of python loops over the entire list each time. If that were the case, this would get out of hand pretty quickly with large lists.

## Problem Two
#### Name:
Binary Representation

#### Description:
Write a function to compute the binary representation of a positive decimal integer. The method should return a ```string```.

#### Example:
```python 
dec_to_bin(6) ==> "110"

dec_to_bin(5) ==> "101"
```
Note : Do not use in-built ```bin()``` function.

#### Solution:
```python
def dec_to_bin(number):
    if number < 2:
        if number == 0:
            return '0'
        return '1'
    str1 = str(dec_to_bin(number/2))
    str2 = str(dec_to_bin(number%2))
    
    return str1 + str2
```

#### Analysis:
I solved this using recursion. The base cases were for anything where the number was less than two because then we can easily return the binary representation. Anything else, I would divide the number by two and add it to the remainder of dividing the number by two.

Now that I'm looking at my solution again, I don't think I need the ```str()``` wrapping around the recursive calls as the base cases return ```strings```.

I'm still practicing my big O analysis, so I'm going to say that this one is O(n) for both time and space again.

## Problem Three
#### Name:
Repeated elements in an array

#### Description:
Write a function - ```duplicate_items``` to find the redundant or repeated items in a list and return them in sorted order. 
This method should return a list of redundant integers in ascending sorted order. 

#### Example:
```python 
duplicate_items([1, 3, 4, 2, 1]) => [1]

duplicate_items([1, 3, 4, 2, 1, 2, 4]) => [1, 2, 4]
```

#### Solution:
```python
def duplicate_items(list_numbers):
    items = []
    duplicates = []
    
    for i in list_numbers:
        if i not in items:
            items.append(i)
        else:
            duplicates.append(i)
    return sorted(duplicates)
```

#### Analysis:
My thoughts were to keep track of two separate ```lists``` and if an item was already inside of one, it must be a duplicate. Once we're done looping through all items in ```list_numbers``` we'll sort the duplicates list and return it.

Again, I'm not sure how python implements the ```not in``` so I'm going to say this is O(n) for both time and space again.

## Problem Four
#### Name:
Fibonacci

#### Description:
The Fibonacci Sequence is the series of numbers: ```0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ... ``` The next number is found by adding up the two numbers before it.
Write a recursive method ```fib(n)``` that returns the ```nth``` Fibonacci number. ```n```is 0 indexed, which means that in the sequence ```0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...```, n == 0 should return 0 and n == 3 should return 2. 
Assume n is less than 15.
Even though this problem asks you to use recursion, more efficient ways to solve it include using an Array, or better still using 3 volatile variables to keep a track of all required values

#### Example:
```python 
fib(0) ==> 0

fib(1) ==> 1

fib(3) ==> 2
```

#### Solution:
```python
def fib(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    
    return fib(n-1) + fib(n-2)
```

#### Analysis:
Fibonacci questions seem to be pretty common in computer science styled tests / exams. Especially when they're trying to teach people about recursion. Obviously, this one requires recursion so that's what I did!

Again, it's pretty straightforward. You build the base cases and then anything else that is not a base case, you recursively call it and add them together. Now that I'm looking at it again while writing this, I could simplify my base case to be:
```python
if n < 2:
    return n
```
C'est la vie!

I would say this is O(n) for time and space as well.

## Problem Five
#### Name:
Horizontal Flip

#### Description:
You are given an m x n 2D image matrix (```List of Lists```) where each integer represents a pixel. Flip it **in-place** along its horizontal axis.

#### Example:
```python
Input image :  
              1 1
              0 0 
Modified to :   
              0 0
              1 1
```

#### Solution:
```python
def flip_horizontal_axis(matrix):
    if len(matrix) >= 1:
        for i, val in enumerate(matrix[0]):
            tmp = matrix[-1][i]
            matrix[-1][i] = val
            matrix[0][i] = tmp
```

#### Analysis:
As long as the array is in fact a multidimensional array, loop through each item in the first list, and swap it with the item in the last list. This is accomplished by creating a ```temp``` variable so when you swap you don't overwrite it.

I would say this is O(n) for time, but given the **in-place** constraints, it's going to be O(1) for space. 

### Summary

So far so good on my challenges. Of course, they're still the level once challenges, so they've not been too difficult at all. One thing that I noticed from [firecode.io](www.firecode.io) is that they used the spaced repetition technique that [Anki](https://ankiweb.net/about) uses. I'm a big fan of this technique, especially because I've always had such a terrible memory. Even utilizing this technique, I still forget so much. It's quite frustrating, but there's nothing I can do about it except embrace and adapt.
