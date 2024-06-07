---
id: Stack
aliases: []
tags: []
---

# Stacks

Stacks are just backwards [[Queue]]s - singly [[Linked Lists|linked Lists]] where we only add and remove at the head ***this is called a LIFO last-in-first-out

Where queues are:
```
 h              t
(a)->(b)->(c)->(d)
```

Stacks are:
```
 t              h
(a)<-(b)<-(c)<-(d)
```

## Adding to a stack

Let's say we have:

...and we wanted to add (e)
```
 t              h
(a)<-(b)<-(c)<-(d)   ...(e)
```
It would be the opposite of queue

```
 t              h
(a)<-(b)<-(c)<-(d)<-(e)
```
Then point head to e
```
 t              h-----
 |              ↓    ↓
(a)<-(b)<-(c)<-(d)<-(e)
```
Then remove old pointer
```
 t                   h
 |              X    ↓
(a)<-(b)<-(c)<-(d)<-(e)
```

## Popping off

Likewise a pop would work with the same logic
```
 t              -----h
 |              ↓    ↓
(a)<-(b)<-(c)<-(d)<-(e)
```
Return e

```
 t              h
 |              ↓     
(a)<-(b)<-(c)<-(d)  (e)->
```

Note: It can be helpful especially in the world of recursion to think of funtion calls as a stack
- It gives you a mental model of what's going on under the hood

## Implementing a Stack

```typescript
type Node<T> = {
    value: T,
    prev?: Node<T>,
}
export default class Stack<T> {
    public length: number;
    private head?: Node<T>;

    constructor() {
        this.head = undefined;
        this.length = 0;
    }

    push(item: T): void {
        const node = {value: item} as Node<T>;

        this.length++;
        if (!this.head){
            this.head = node;
            return;
        }

        node.prev = this.head;
        this.head = node;
    }
    pop(): T | undefined {
        this.length = Math.max(0, this.length - 1);
        if (this.length === 0){
            const head = this.head;
            this.head = undefined;
            return head?.value;
        }
        const head = this.head as Node<T>;
        this.head = head.prev;
        return head.value;
    }
    peek(): T | undefined {
        return this.head?.value;
    }
}
```
