---
id: Binary Search Example
aliases: []
tags:
  - "-Example"
---
# Binary Search Example

Say we wanted to implement a binary search

How would we do it?

Well we first need:
- An **ordered** array
- A value to search for
- The bounds of our search

Then we could say:
1. Find the middle of the array
2. Is the value we are looking for in the middle?
3. If not, is the value we are looking for less than or greater than the middle?
4. If less than, search the left half of the array
5. If greater than, search the right half of the array
6. Repeat until we find the value or the bounds of our search are equal

```typescript
export default function bs_list(haystack: number[], needle: number): boolean {

    let lo = 0;
    let hi = haystack.length;
    do {
        const m = Math.floor((lo + hi) / 2);
        const v = haystack[m];

        if (v == needle) {
            return true;
        } else if (v > needle) {
            hi = m;
        } else if (v < needle) {
            lo = m + 1;
        }

    } while (lo < hi);
    return false;

}
```
