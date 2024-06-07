---
id: Recursion
aliases: []
tags: []
---

# Recursion

The simplest way to thisk of recursion is a function that calls itself until the problem is solved.
This usually inolves what is known as a base case, a condition that stops the recursion.

The simplest example
```typescript
funtion foo(n: number): number {
  //base case
  if (n === 0) {
    return 0;
  }
  //recursive case
  return n + foo(n - 1);
}
```

