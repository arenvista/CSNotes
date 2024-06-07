# Dynamic Programming 

The basic premise of dynamic programming is to identify and solve subproblems and then bringing them together to solve the larger problem.

## Longest Increasing Subsequenc (LIS)
For a sequence of `a1, a2,... an` elements find the length of the longest increasing subsequesnce  `ai1, ai2,...aik` 

Constraints: i1 < i2 < ... < ik; ai1 < ai2 < ... < aik
u

For example:
- Given LIS([3 1 8 2 5]) 


```
        2nd
        ↓
([3 1 8 2 5])  -> 3
    ↑     ↑
    1st   3rd
```

We will focus on the length of the LIS

***Approach 1: Visualize Examples***
