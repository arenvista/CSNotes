# How To Convert Gray Code to Binary and Binary to Gray Code
|------|--------|-----------|
| Dec. | Binary | Gray Code |
|------|--------|-----------|
| 0    | 000    | 000       |
| 1    | 001    | 001       |
| 2    | 010    | 011       |
| 3    | 011    | 010       |
| 4    | 100    | 110       |
| 5    | 101    | 111       |
| 6    | 110    | 101       |
| 7    | 111    | 100       |
|------|--------|-----------|

Let's start with a simple example, say we have 011 in binary, and we want to convert it to Gray code.
```
  B   ->   G
 011      
```
We would want to first focus on the most significat bit, (the leftmost bit), and copy it
```
  B   ->   G
 (0)11     0
  ↑        ↑
```
Then we would want to compare the two bits, and if they are the same, we would write 0, otherwise we would write 1.
```
  B   ->   G
 [01]1     0
  ↑↑        

if [00] || [11] -> 0
elif [01] || [10] -> 1

  B   ->   G
 [01]1     01
           ↑      
```
Then we shift the view box by one bit to the right and repeat the process
```
  B   ->   G
 0[11]     01
   ↑↑      

if [00] || [11] -> 0
elif [01] || [10] -> 1

  B   ->   G
 0[11]     010
             ↑     
```

