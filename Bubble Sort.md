---
id: Bubble Sort
aliases: []
tags: []
---

# Bubble Sort

If an airplane was going down - you could write a bubble sort algorithm on the back of a napkin before you hit the ground.

The math-y definition of a **sorted** array is:
[                                   ]
|                                   |
0                                   N

- For any Xi <= Xi + 1

The way buble sort works is that it starts at the 0th index -> end of the array
- It then asks the guy next to him (+1 index) are you larger?
    - If so swap them

Let's consider the following 
```
[1,3,7,4,2]

[1,3,7,4,2]
 | |

[1,3,7,4,2]
   | |

[1,3,7,4,2]
     | |
     S S
     
[1,3,4,7,2]
       | |
       S S

[1,3,4,2,7] <- End of first loop
```

Note the position of the n-th element:
[1,3,4,2,7]
         |-> Notice how bubble sort 'bubbles' up the largest number to the top of the list

Let's do the next itteration
```
[1,3,4,2,7] 
 |
[1,3,4,2,7] 
   |
[1,3,4,2,7] 
     | |
     S S

[1,3,2,4,7] 
```
And again...
```
[1,3,2,4,7] 
 | 

[1,3,2,4,7] 
   |

[1,3,2,4,7] 
   | |
   S S

[1,2,3,4,7] 
```
And lastly we would be left with just the first position to sort - but an array of size 1 is always sorted

What is the time complexity?
- Notice how the number of steps decrease by n-1 in each itteration: as we know the largest value will be in the end

Here's a story to help you remember:

Gauss was a student and a bit of an asshole so one day his teacher asked him to add all the numbers from 1 to 100

Gauss being the genious that he is realized a pattern appears if we take this question and look at both ends

Really we have a list of numbers from 1..100

What happens if we add: 

1..100 = 101
2..99  = 101
3..98  = 101

It seems that every itteration adds to the same value since as one value goes down another goes up

And it makes sense that this could continue until we covered all possible numbers; which would mean these two numbers would meet in the middle

50..51 = 101

So this itteration happens 50 times and the answer is 101 (sum of each loop) * 50 (number of loops) 

But we can generalize this!
- We were ***given*** a data set of 100

So we could say 101 * 50 here is the same as (n + 1) n/2
- We can drop the constants and we would be left with n^2

# Implementation

```typescript
export default function bubble_sort(arr: number[]): void {
    for (let i = 0; i < arr.length; ++i) {
        for (let j = 0; j < arr.length -1 -i; j++) {
            if (arr[j] > arr[j + 1]){
                const tmp = arr[j];
                arr[j] = arr[j + 1]
                arr[j + 1] = tmp
            }
        }
    }
}
```
