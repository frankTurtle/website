---
layout: single
title: 'Day Eleven'
date: 2019-04-14 09:19:00 -0400
categories: prep interview algorithms firecode
---

# 100 days challenge -- Day Eleven

Well, so far so good! I've been able to complete Thirteen problems so far. I've been bogged down finishin my last AI assignment, but I still manage to try and get practice in at least once per day

## Problem Seven
#### Name:
Flip It!

#### Description:
You are given an m x n 2D image matrix (```List of Lists```) where each integer represents a pixel. Flip it in-place along its vertical axis.

#### Example:
```python 
Input image :
1 0              
1 0 

Modified to :
0 1              
0 1
```

#### Solution:
```python
def flip_vertical_axis(matrix):
    for row in matrix:
        row[:] = row[::-1]
```

#### Analysis:
You've to love the power of python slicing again! I feel like this answer might be a little bit of a cop-out because of the power of slicing. I'm considering doing it again without slicing, or possibly in another language.

I would say that this would be O(n) runtime and O(1) for space.

## Problem Eight
#### Name:
Reverse a String

#### Description:
Write a function that takes in a ```string``` and returns the reversed version of the ```string```.

#### Example:
```python 
reverse_string("abcde") -> "edcba"

reverse_string("1") -> "1"

reverse_string("") -> ""

reverse_string("madam") -> "madam"
```

#### Solution:
```python
def reverse_string(a_string):
    return a_string[::-1]
```

#### Analysis:
Another cop-out. I don't think this would go over well in an interview, maybe though?

I would say that this would be O(n) runtime and O(1) for space.

## Problem Nine
#### Name:
Merge Integer Ranges

#### Description:
Given a sorted list of integer ranges, merge all overlapping ranges.

#### Example:
```python 
Input  : [[1,10], [5,8], [8,15]]
Output : [[1,15]]
```

#### Solution:
```python
def merge_ranges(input_range_list):
    tmp = input_range_list[0]
    output = []
    
    for range in input_range_list:
        if range.lower_bound <= tmp.upper_bound:
            if range.upper_bound >= tmp.upper_bound:
                tmp.upper_bound = range.upper_bound
            else:
                continue
        else:
            output.append(tmp)
            tmp = range
    output.append(tmp)
    return output
```

#### Analysis:
This one was a bit challenging for me.

I would say that this would be O(n) runtime and O(n) for space.

## Problem Ten
#### Name:
Reverse a Singly Linked List

#### Description:
Given a singly linked list, write a method to perform In-place reversal.

#### Example:
```python 
1->2->3 ==> 3->2->1
```

#### Solution:
```python
class SinglyLinkedList:
    #constructor
    def __init__(self):
        self.head = None
        
    #method for setting the head of the Linked List
    def setHead(self,head):
        self.head = head
                      
    def reverse(self):
        last = None
        curr = self.head
        
        while curr:
            tmp = curr.getNext()
            curr.setNext(last)
            last = curr
            curr = tmp
        self.head = last
```

#### Analysis:
This one was also a bit of a challenge. I never really use linked lists, so I had to work pretty hard on this. Code wise, it wasn't too difficult, but thinking about the logic and how all the components worked together was completely new for me. I guess that's the point of all this practice though, right?

I would say that this would be O(n) runtime.

## Problem Eleven
#### Name:
Numbers and Ranges

#### Description:
Given a sorted list and an input number as inputs, write a function to return a ```Range``` object, consisting of the indices of the first and last occurrences of the input number in the list. Check out the Use Me section to examine the structure of the ```Range``` class.

Note: The List can have duplicate numbers. The indices within the ```Range``` object should be zero based.

#### Example:
```python 
Input List  : [1,2,5,5,8,8,10]
Input Number : 8
Output : [4,5]

Input List  : [1,2,5,5,8,8,10]
Input Number : 2
Output : [1,1]
```

#### Solution:
```python
def find_range(input_list,input_number):
    low, high = 0, 0
    l_done = False
    
    for i, val in enumerate(input_list):
        if val == input_number:
            if not l_done:
                low, high = i, i
                l_done = True
            else:
                high = i
    return Range(low, high)
```

#### Analysis:
My code is not good. Yes, it solves the problem. It's just not efficient. The way mine is written is O(n) runtime - worse case. One of the things that I should have picked up on was the keyword *sorted*. This is a good hint to use something like a binary search. I'm going to need to re-implement this to make it more efficient. With the new implementation it should be O(log n) runtime, and O(1) space.

## Problem Twelve
#### Name:
Unique chars in a String

#### Description:
Write a function that takes in an input ```string``` and returns ```True``` if all the characters in the ```string``` are unique, ```False``` if there is even a single repeated character.

#### Example:
```python 
unique_chars_in_string("abcde") -> True

unique_chars_in_string("aa") -> False

unique_chars_in_string("") -> True
```

#### Solution:
```python
def unique_chars_in_string(input_string):
    return len(set(input_string)) == len(input_string)
```

#### Analysis:
Oh, the magic of python, yet again. There are other languages that have this power, I'm sure. I just do not know them!

This one was pretty straightforward, sets in python remove duplicates. So checking to see if the lengths are the same after making one a set, will give you the answer.

I would say this is O(n) runtime and O(n) space.

## Problem Thirteen
#### Name:
Count the Leaves!

#### Description:
Write a function to find the total number of leaf nodes in a binary tree. A node is described as a leaf node if it doesn't have any children. If there are no leaf nodes, return ```0```.

#### Example:
```python 
       1
      / \
     2   3     
    / \ / \
   4  5 6  7
  / \
 8   9     
==> no. of leaves = 5
```

#### Solution:
```python
class BinaryTree:
    def __init__(self, root_node = None):
            self.root = root_node

    def number_of_leaves(self,root):
        if not root:
            return 0
            
        if not root.left_child and not root.right_child:
            return 1
            
        return self.number_of_leaves(root.left_child) + self.number_of_leaves(root.right_child)
```

#### Analysis:
Good ol' recursion! First thing it so check if the data passed in exists. When the left and right child are empty, that means you're at the leaf. You should return one!

If not, keep recursively calling it together and add together.

I would say it's O(n) runtime and O(1) for space.

## Problem Fourteen
#### Name:
Bubble Sort

#### Description:
Write a function that takes in a list of ints and uses 
the Bubble Sort algorithm to sort the list 'in place' in ascending order. The method should return the same, in-place sorted list.
Note: Bubble sort is one of the most inefficient ways to sort a large list of integers. Nevertheless, it is an interview favorite.
Bubble sort has a time complexity of O(n2). However, if the 
sample size is small, bubble sort provides a simple implementation of a classic sorting algorithm. 

#### Example:
```python 
bubble_sort([5, 4, 3]) -> [3, 4, 5]

bubble_sort([3]) -> [3]

bubble_sort([]) -> []

[] -> [Empty] List 
```

#### Solution:
```python
def bubble_sort(a_list):
    if not a_list:
        return []
    
    mx = len(a_list) - 1
    
    for i in range(mx):
        for j in range(mx):
            if j + 1 > mx:
                continue
            if a_list[j] > a_list[j+1]:
                a_list[j], a_list[j+1] = a_list[j+1], a_list[j]
    
    return a_list
```

#### Analysis:
I have never actually written a bubble sort before. Mainly because I know it's probably the most inefficient sorting algorithm there is. It never even occured to me to that it might be a good interview question!

As you can see, its pretty terrible. If the size of the list is huge, you're going to have a bad time. 

I would say it's O(n^2) runtime and O(1) for space.