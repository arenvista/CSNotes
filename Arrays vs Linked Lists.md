---
id: Arrays vs Linked Lists
aliases: []
tags: []
---
# Arrays vs Linked Lists
Arrays 
- give you direct access to any element in the array (indexing)
- have a fixed size
- types of elements in the array must be the same
- no way to really insert or delete elements in the middle of the array without shifting elements around
- all operations are O(1) except for inserting and deleting elements
- all memory is allocated at once

Linked Lists
- has nothing to begin with
- memory is allocated as you go
- can insert and delete elements in the middle of the list without shifting elements around
- no direct access to elements in the list, must traverse the list to find the element
- Limited to ***[[Search|Linear Search]]***

Can we do better? Yes, we can! Check out [[ArrayList]]
```
