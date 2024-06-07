---
id: Binary Search
aliases: []
tags:
  - "-Definition"
---

# Binary Search

Presume we have an **ordered** array of elements from 0 -> n
```
[0, ..., n]

If this is the case and we wanted to search for some value in the array, we can use a binaryksearchkalgorithm.

- One thing that we could do is this

[0,...(n/2),...,n]
|________|
    1/2th of the array -> Is the value in this range?
                                    |-> No -> Check the next 1/2th

[(n/2),...,n]
  |________|
    1/2 of the array -> Is the value in this range?
                                    |-> No -> Check the next 1/2h
```
The idea is to keep walking up by section up or down the ordered array until we find the value we are looking for.

This gives us a time complexity of O(log n) which is much better than O(n) for linear search.

[[Binary Search Example]]
