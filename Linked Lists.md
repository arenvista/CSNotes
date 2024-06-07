---
id: Linked Lists
aliases: []
tags: []
---

# Linked Lists

Linked lists are called a node-based data structure. Each node contains a value and a reference to the next node in the sequence.

[[Singly Linked List]]
[a]->[b]->[c]->[d]->[e] <- node<t> 
 |->head (first element    val:T   
                           next?:Node<T>

Notice how the this data structure is ***unidirectional***. This means that you can only traverse the list in one direction.

[[Doubly Linked List]]
[a]<->[b]<->[c]<->[d]<->[e] <- node<t> 
 |->head (first element    val:T   
                           next?:Node<T>
                           prev?:Node<T>
We can include a ***prev*** pointer in the node to allow for traversal in both directions

Let's talk about time & space complexity:

## [[Time Complexity of Linked Lists]]

Here's an [[Example Implementation of Linked List]]

***Traversals are the big things here costly and can be aided with refrences***

