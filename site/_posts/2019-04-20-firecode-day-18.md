---
layout: single
title: 'Day Eighteen'
date: 2019-04-20 14:08:00 -0400
categories: prep interview algorithms firecode
---

# 100 days challenge -- Day Eighteen

One of the best things about Firecode, and something that I did not know about, is that they use one of my favorite memory techniques - [Spaced Repetition](https://en.wikipedia.org/wiki/Spaced_repetition). I have an awful memory, especially when it comes to memorization. While programming problems are not about memorization, there is the element of memorization involved. When you repeatedly practice similar problems it will make recognizing and solving them easier in the future.

That being said, here are the latest ones I've been able to work through. 

## Problem Sixteen
#### Name:
Insert Stars

#### Description:
Given a string, recursively compute a new ```string``` where identical, adjacent characters get separated with a "*".  

#### Example:
```python 
insert_star_between_pairs("cac") ==> "cac"

insert_star_between_pairs("cc") ==> "c*c"
```

#### Solution:
```python
def insert_star_between_pairs(a_string):
    if a_string is None or len(a_string) <= 1:
        return a_string
    
    if a_string[0] == a_string[1]:
        a_string = a_string[:1] + '*' + a_string[1:]
        
    return a_string[:1] + insert_star_between_pairs(a_string[1:])
```

#### Analysis:
The obvious test's at the beginning are looking for an empty input or one that is too small. We need a minimum of two characters for the rest of the code to do anything meaningful. We're essentially slicing up the string over and over and if the two adjacent characters are equal, drop a '*' between them.

I would say that this would be O(n) runtime and O(n) for space as well. Although, I'm not positive on how the space complexity changes with recursion. I need to add that to my list of things to figure out. And come to think of it, ```strings``` are immutable in python, so I bet the runtime would be O(n^2) because it's essentially creating a brand new string each time there is a star inserted.

## Problem Seventeen
#### Name:
Max Gain

#### Description:
Given an list of integers, write a method - ```max_gain``` - that returns the maximum gain. Maximum Gain is defined as the maximum difference between 2 elements in a list such that the larger element appears after the smaller element. If no gain is possible, return 0.

#### Example:
```python 
max_gain([100,40,20,10]) ==> 0
max_gain([0,50,10,100,30]) ==> 100
```

#### Solution:
```python
def max_gain(input_list):
    low, high = (input_list[0], 0), (input_list[0], 0)
    
    for i, val in enumerate(input_list):
        if val < low[0] and i < low[1]:
            low = (val, i)
        if val > high[0] and i > high[1]:
            high = (val, i)
            
    if low[1] == 0 and high[1] == 0:
        return 0
        
    return high[0] - low[0]
```

#### Analysis:
I used some ```tuples``` on this to keep track of the index and the value for the low / high values. I loop through the entire list and update the values / indices of low / high respectively. At the end, if the index of either of them is still zero, then there was no gain possible so I return ```0```. 

I would say that this would be O(n) runtime because I have to loop through each value in the list and I'm not positive on the space complexity. It only keeps track of at most two ```tuples``` so there is some additional memory usage, but it's fairly negligible in my mind. The numbers themselves could be gigantic, and for that matter, so could the index. But, it's still just two numbers. I'm not sure to be honest. I would still say it's O(1). 

## Problem Eighteen
#### Name:
Insert at the front of a singly linked list

#### Description:
The title says it all, but --> Write a function to insert a node at the front of a Singly Linked-List

#### Example:
```python 
LinkedList: 1->2 , Head = 1

insert_at_front(1) ==> 1->1->2

insert_at_front(2) ==> 2->1->2

insert_at_front(3) ==> 3->1->2
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
                      
    # Method for inserting a new node at the start of a Linked List   
    def insert_at_front(self,data):
        new_head = Node()
        new_head.setData(data)
        new_head.setNext(self.head)
        self.setHead(new_head)
```

#### Analysis:
This one was pretty straight forward. You're given the data and you need to insert it into the front of the linked list. You first create the new ```Node``` - side note, I would like the ```Node``` classes constructor to be able to accept data. I think I mentioned that in another analysis post. Then you would set the 'pointer' to the current head of the linked list, and reset the head.

I would say that this would be O(1) runtime and O(1) for space.