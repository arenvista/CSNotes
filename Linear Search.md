---
id: Linear Search
aliases: []
tags:
  - "- Definition"
---

# Linear Search
Consider we have some array 

[0,...,n]

- That extends from 0 to n
- We want to call search(arr, value) that returns the index of the value in the array

The simplest way to do this is to iterate through the array and check each value

[0] == value ? No -> [1] == value ? No -> [2] == value ? Yes -> return 2
