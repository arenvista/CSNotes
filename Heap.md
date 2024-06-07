---
id: Heap
aliases: []
tags: []
---

# The Heap DataStructure
The simplest way to put it is a binary tree where every child and grand child is smaller (MaxHeap), or larger (MinHeap) than the current node
- Whenever a ode is added, we must adjust the tree
- Whenever a node is deleted, we must adjust the tree
- There is no traversing the tree
- a binary tree or heap is typically a complete tree
     - always filled from left to right with no gaps

## How to add a new node
![heap001.png](assets/imgs/heap001.png)

## How to delete a new node
![heap003.png](assets/imgs/heap003.png)
This sounds great and all but how do we get to a node in the heap?

### Insert/Delete Time Complexity
The worst case is bubbling up/down the entire tree
-  log(n) time complexity - since each layer of the tree is half the size of the previous layer

## Traversal / Parent Child Relationship
![heap004.png](assets/imgs/heap004.png)
We need to reimagine how we store a tree.
- Let's put an index on each node

