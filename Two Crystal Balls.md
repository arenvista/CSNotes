---
id: Two Crystal Balls
aliases: []
tags:
  - "-Problem"
---
Consider the following:
- Given two crystal balls that will break if dropped from high enough distane
- Determine the exact height at which the balls will break

Let's discuss our options:
- [[Linear Search]]
- [[Binary Search]]

Which one would you choose and why?

First, let's explore the problem a bit more.

Really we can conceptualize this problem as a tower of floors, these floors can represent cells in an array. 
```
   |-> Floor 1
[false][false][false][false][false][true][true][true][true][true] <- Where all statments are false (no break) until the ball hits the critical point and will continue to break (true).
                                     |-> The question is asking where is this point?
```

** We need to be able to jump as oppossed to itterate through each floor. **
- In this case we could walk each step by sqrt(n) where n is the number of floors.

We jump from 0 -> sqrt(n) until it breaks and then we can walk back to the previous section and walk though a section the size of sqrt(n) until we find the exact floor.
This gives us O(sqrt(n)) time complexity.
