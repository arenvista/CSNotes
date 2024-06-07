---
id: Queue
aliases: []
tags: []
---
Queue: This is probably the most common data structure that I have implemented in many languages.

These guys are just [[Linked Lists|linked Lists]] with a  ***FIFO*** First-In-First-Out structure  
***They are singly linked list where we only add at the tail and remove at the head***

```
    head                 tail
     ↓                    ↓
    (a) -> (b) -> (c) -> (d)
```
Just like the brits call it a queue, we call a line - what happens when you want to order in a resturant and there's a line?

## Adding to a queue
You get in the back of the line.
Consider yourself to be `(e)` in this case

Here we update (d) to point to (e) and update the pointer tail to the new end of the list (e)
```
    head                 tail ---↴
     ↓                    ↓      ↓
    (a) -> (b) -> (c) -> (d) -> (e)
```

Then we can remove the pointer to the previous tail
```
    head                        tail 
     ↓                    X      ↓
    (a) -> (b) -> (c) -> (d) -> (e)
```

## Removing from queue
Now let's assume we were deleting (a)

First lets update the pointer of head
```
    head ____                   tail 
     ↓      ↓                    ↓
    (a) -> (b) -> (c) -> (d) -> (e)
```

Then we can remove the old pointers
```
    head ____                   tail 
     X      ↓                    ↓
    (a)  X (b) -> (c) -> (d) -> (e)
```
And that's it! That's a queue it's just a linked list with restrictions

Now lets [[Implementing Queue]]
