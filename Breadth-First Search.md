---
id: Breadth-First Search
aliases: []
tags: []
---

# Breadth-First Search 
![Breadth-First-Search.png](~/Documents/Learning/CSNotes/assets/imgs/Breadth-First-Search.png)

## Psuedo Code Implementation
while q.full()
next = q.dequeue()
q.enqueue(next.left)
q.enqueue(next.right)
