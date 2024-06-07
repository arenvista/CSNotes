Let's say we have 6 people: A, B, C, D, E, F. We want to form a group of 3 people. How many different ways can we do this?

We have 3 chairs:

```
_ _ _
1 2 3
```

Well there's 6 people that could be in chair 1
```
6
_ _ _
1 2 3
```
Well there's 5 possible people that could sit in chair 2, since someone has to be in chair 1
```
6 5
_ _ _
1 2 3
```
Lastly, there's 4 possible people that could sit in chair 3, since someone has to be in chair 1 and chair 2
```
6 5 4
_ _ _
1 2 3
```
So there are 6*5*4 = 120 different ways to form a group of 3 people from 6 people.
- 120 permutations

But what exactly are permutations? Permutations are the number of ways you can arrange a group of items. 

For example:
- abc
- acb
- bac
- bca
- cab
- cba

Are all the ***same six people** but in different orders - this is considered as 4 distinct permutations but as ***only one combination***.

So how many combinations are there?

Well notice how:
- abc
- acb
- bac
- bca
- cab
- cba

There are 6 unique ways to arrange a group of 6 people. In other words we can fill the same 3 chairs with unique order 6 differnet ways. 
So we could take the total number of permutations and divide by the number of ways to arrange the group of people to get the number of combinations.

```
120 / 6 = 20
```
