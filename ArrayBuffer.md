---
id: ArrayBuffer
aliases: []
tags: []
---

Consider an allocated piece of memory like an array...
```
0[null][    ][    ][    ][    ][    ][    ][    ][    ][null]N
          ↑                                        ↑
         HEAD                                     TAIL
```
It's another list, but this time instead of either head or tail being defined at either 0 or N they are just refrences to some index position within this allocated memory
- indecios out of bounds are defined by the nulls

So removing from the front of the list is just as simple as moving head forward and changing the value at the old head to null
Likewise with tail, just bring them to the center.

This brings pushing and popping to O(1) time complexity

What if we go off the edge?
```
        TAIL                               HEAD
         ↓                                   ↓    
0[ XX ][ XX ][    ][    ][    ][    ][    ][ XX ][ XX ][ XX ]N
    ↑_____________________________________________________|
              arraybuffer.tail%len lets us wrap around

```

What's a lil confusing is resizing. When dealing with ring buffers when you shift or unshift you're not jush getting any element
You're getting the last element added to the head.

So what do we do when tail exceeds head?
- We can just create a new arraybuffer of larger capacity and start at head and copy all the elements over
