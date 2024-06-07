---
id: BST
aliases: []
tags: []
---

# Binary Search Tree
Binary search trees are a type of binary tree that follow one rule:
![bst001.png](assets/imgs/bst001.png)

Traversing these trees by nature of their strong ordering is akin to traversing a sorted array.
![bst002.png](assets/imgs/bst002.png)

## Implmenting Find
Find is a simple opperation
![bst0f.png](assets/imgs/bst0f.png)

## Implementing Insert
Insertion is still simple, and similar to linked lists
![bst003.png](assets/imgs/bst003.png)

## Implementing Delete
Deletion is more complex and needs to divided into cases:

### Case 1: Node has no children
The simplest case is when the node to be deleted has no children. In this case, we simply remove the node from the tree.
![bst004.png](assets/imgs/bst004.png)

### Case 2: Node has one child
In a single child case, we can simply remove the node and replace it with its child like so.
![bst005.png](assets/imgs/bst005.png)

### Case 3: Node has two children
Note in this example we used the smallest side, but we could have used the largest side as well.
![bst006.png](assets/imgs/bst006.png)



