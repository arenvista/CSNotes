---
id: Big-O Notation Dosent Care About restraints
aliases: []
tags: []
---

# Big-O Notation Dosent Care About restraints

Big-O notation doesn't care about constants because big-O notation only describes the long-term growth rate of functions, rather than their absolute magnitudes. Multiplying a function by a constant only influences its growth rate by a constant amount, so linear functions still grow linearly, logarithmic functions still grow logarithmically, exponential functions still grow exponentially, etc. Since these categories aren't affected by constants, it doesn't matter that we drop the constants.

That said, those constants are absolutely significant! A function whose runtime is 10100n will be way slower than a function whose runtime is just n. A function whose runtime is n2 / 2 will be faster than a function whose runtime is just n2. The fact that the first two functions are both O(n) and the second two are O(n2) doesn't change the fact that they don't run in the same amount of time, since that's not what big-O notation is designed for. O notation is good for determining whether in the long term one function will be bigger than another. Even though 10100n is a colossally huge value for any n > 0, that function is O(n) and so for large enough n eventually it will beat the function whose runtime is n2 / 2 because that function is O(n2).

In summary - since big-O only talks about relative classes of growth rates, it ignores the constant factor. However, those constants are absolutely significant; they just aren't relevant to an asymptotic analysis.

Let's do another example. What would you expect the time complexity of the following code snippet to be?
