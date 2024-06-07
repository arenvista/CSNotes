---
id: ArrayList
aliases: []
tags: []
---

# ArrayList

Can we have an array access with the ability to grow?

Yes! We just have to implement it ourselves. This is where the `ArrayList` comes in. 

An arraylist is a an [[Arrays|array]] of some generic type `T` that can grow and shrink as needed.  

Let's say we have an array of size 3.
```c
int myArrayList[3];
myArrayList[0] = 2;
```
Here we are creating the following:
```
[2, _, _]
```
We can say that we have an array length of 1 but a capacity of 3.

Then if we wanted to add another number to the list we can define some method to adjust the length of the array if in bounds of the capacity. 
## [[Stack#adding-to-a-stack|Array Push]]

```c
void add(int value){
    if (length == capacity){
        //resize the array
    }
    myArrayList[length] = value;
    length++;
}
```
We're ***creating a push method on top of an array*** - it's ***using the array is the fundemental data structure instead of a node***

Note this is a constant time operation since we are working with an array 
- Arrays initialize all memory at once
- Arrays are contiguous in memory
- Arrays are indexed
- Allows for direct access to elements in the array
    - This operation is O(1)


What happens if we hit the capacity of the array? We can resize the array by creating a new array with a larger capacity and copying the elements over. 

```c
void resize(){
    int *newArray = new int[capacity * 2];
    for (int i = 0; i < length; i++){
        newArray[i] = myArrayList[i];
    }
    delete[] myArrayList;
    myArrayList = newArray;
    capacity *= 2;
}
```
## [[Queue#adding-to-a-queue|Array Enqueue]]
```
[2, 3, 5, _, _, _]
```
So how could we enqueue (write to the front of the array)?
- Recall that in an array there is no way to insert like in a [[1713366142-IMCX|Linked List]] without shifting elements around.
     - ***In an array, we have to shift all elements to the right to make room for the new element - then insert the new element to prevent overwriting the old data.***

This is why we have to care about ***where we insert into an arrraylist*** because adding to the end is much faster than adding to the front - as to add to the front requires shifting all elements to the right which is an O(n) operation.

## [[Queue#removing-from-queue|Array Dequeue]]
What do you thinj would happen if we dequeued from the array?

```
[2, 3, 5, _, _, _]
```
The same problem occurs as in the enqueue operation. We have to shift all elements to the left to fill the gap left by the dequeued element.

```
[_, 3, 5, _, _, _]
```
...and then we have to shift all elements to the left again to fill the gap left by the dequeued element.

```
[3, 5, _, _, _, _]
```
This just like enqueue is an O(n) operation. 

***Hence arraylists are really bad at enqueuing and dequeuing elements (adding/removing at the front) but really good at push and pop (adding/removing at the end).***

So when to use an arraylist over a [[Linked Lists|linked Lists]]?

as always it depends on the use case.

- Linked lists are better for adding and removing elements at the front of the list
- Arraylists are better at adding and removing elements at the end of the list
- Arraylists can be indexed and accessed in constant time
- Linked lists are not indexed and require traversal to access elements

***There is always a cost somewhere to the system***
