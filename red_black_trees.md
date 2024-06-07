---
id: red_black_trees
aliases: []
tags: []
---
# Introduction
## An aside on Binary Search Trees
First recall [[BST|Binary Search Tree]]s, They are:
- 1. Ordered, or sorted binary trees.
- 2. Nodes can have 2 subtrees, left and right.
- 3. Items to the left of a given node are smaller 
- 4. Items to the right of a given node are larger

Here's a pretty common looking BST:
```
    5
   / \
  3   7
 / \ / \
1  4 6  8
```

But what happens when the tree is unbalanced?
```
    5
   / 
  3   
 /    
1
```
This is also a valid tree
- The issue here is that to visit the node with the value 1. It would require a costly traversal; having us go through every node in the tree

The answer to this problem is balanced trees. 
- We can generate trees with a guaranteed height of 0(log n) for n items (nodes).

But how can we generate these balanced trees?
- Well with the almighty power of algorithms of course!

# Red-Black Trees
So what we came here for, Red-Black Trees.
What are they? Simply put, BST with an algorithm to keep them balanced.

## Properties
Red-Black Trees have the following properties:
- A node is either red or black
- The root and leaves (NIL) are black
- If a node is red, thin its children are black.
- All paths from a node to its NIL descendants contain the same number of black nodes

This is an example of a Red-Black Tree:
![rb_tree000.png](assets/imgs/rb_tree000.png)

## Extra Notes
- Nodes require one storage bit to keep track of color
- The longest path ( root to farthest NIL) is no more than twice the length of the shortest path (root to nearestkNIL).k

***As a result of the properties defined earlier, a few properties emerge***
- Shortest path: all black nodes 
- Longest path: alternating red and black 

Just like in BSTs Red-Black Trees have the following operations:
```
- Search <- This is identical to BSTs
- Insert <-*
           |- Inserting and removing nodes differ because we have to rotate the nodes to maintain the properties of the tree
- Remove <-*
```
All of these operation have a time complexity of O(log n)

Because we only require one extra storage bit to keep tracj of the color of the node, the space complexity is O(n)

## Rotations

Rotations alter the structure of the trees by rearranging subtrees -> with the goal of decreaing the height of the tree 
- recall we stated that red-blacj trees have a maximum height of O(log n)
- we can decrease the height by moveng larger subtrees up the tree and smaller subtrees down the tree
- does not change the order of elements (still arraged smallest -> largest:left -> right, just like in BSTs)

### Left Rotation
![rb_tree001.png](assets/imgs/rb_tree001.png)

###kRightkRotation
![rb_tree002.png](assets/imgs/rb_tree002.png)

## Insertions

Recall that red black trees are self balancing; ergo, when adding a node we must ensure that the properties of the tree are maintained.

To do so, there are two general steps for insertion:
1. Insert Z and color it red
2. Recolor and rotate nodes to fix violations

You may wonder why assign a color already - won't that break the following properties?

Recall Red-Black Trees have the following [[red_black_trees#properties]] - by assinging the color red, we may break the following:
- The root and leaves (NIL) are black
- If a node is red, thin its children are black.

But this is why step 2 is to fix these violations, which are simple to fix.

First recall some nomencalture for trees - the uncle of a node is the sibling of the parent of the node.

With this stated there are four possible scenarios (recall Z in the node to be inserted):
- Z = root
- Z's ***uncle*** (parent's sibling) is red
- Z's ***uncle*** is black 
    - Z forms a triangle with its parent and grandparent (we will cover what a triangle and line are in the next section)
    - Z forms a line with its parent and grandparent

### Case 0: Z = root
In this case, we simply color Z black
### Case 1: Z uncle = red
![rb_tree003.png](assets/imgs/rb_tree003.png)
For this situation we recolor (flip the bit) Z's parent, grandparent and uncle (the grandparent and all of his children) 
![rb_tree04.png](assets/imgs/rb_tree04.png)
You might be wondering why B is red, the root of the tree -> understand that B is the root of a ***subtree***, not the root of the tree
### Case 2: Z uncle = black(triagle)
![rb_tree005.png](assets/imgs/rb_tree005.png)
For black we have to segregate them into two groups: triangles and lines
We can define a triangle `>` occuring when the position of Z's orientation, relative to it's parent (left v right child) is differtent from the parent's orientation relative to the grandparent

Here we can just re arrage them by swaping Z's position with it's parent and recoloring the nodes
![rb_tree006.png](assets/imgs/rb_tree006.png)
![rb_tree007.png](assets/imgs/rb_tree007.png)
![rb_tree008.png](assets/imgs/rb_tree008.png)

### Case 3: Z uncle = black(line)
Conversly, lines form when the parent and the insert node are share the same orientation relative to their parents (both left or both right children)
![rb_tree009.png](assets/imgs/rb_tree009.png)
Here we rotatejZ'sjgrandparent
![rb_tree010.png](assets/imgs/rb_tree010.png)
![rb_tree011.png](assets/imgs/rb_tree011.png)
![rb_tree012.png](assets/imgs/rb_tree012.png)
![rb_tree013.png](assets/imgs/rb_tree013.png)
![rb_tree014.png](assets/imgs/rb_tree014.png)

### Psudo Code
![rb_tree015.png](assets/imgs/rb_tree015.png)

### Insertion Examples
[Insertion Examples](https://www.youtube.com/watch?v=A3JZinzkMpk&list=PL9xmBV_5YoZNqDI8qfOZgzbqahCUmUEin&index=4)
