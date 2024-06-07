---
id: regex
aliases: []
tags: []
---

# Regular Expressions

```
The fat cat ran down the street.
It was searching for a mouse to eat.
```

In the expression s/e+/  the e+ means one or more e's. The expression will match the following:

```
The* fat cat ran down the* stre*e*t.
It was se*arching for a mouse* to e*at.
```
In the expression s/e+a?/  the a? means `optionally` match an a. This means **if** there is an a, include it in the match. The expression include:
```
s*ear*ching
```

In the expression s/re*/ the e* is like a combo of e+ and e? it means if there's an e include it, but if there's more than one e include them all. The expression will match:
```
st*ree*t
```

Another important operator is the `.` operator. The `.` operator matches any character. So the expression s/.at/ will match:
```
fat cat eat
```

We can also look for any word character using the `\w` operator. The expression s/\w/ will match everything here but the spaces and \n for example
- We can even specify the maximium and minimum number of characters we want to match. For example, s/\w{3,5}/ will match any word that is between 3 and 5 characters long.

If we wanted to select for whitespace we could use the `\s` operator

We can also break down our search term into by using the [] /[fc]at/ will match fat and cat since we are saying to find any word starting with f or c and ending with at.
- We can even express these as ranges /[a-z]at/ will match any word that starts with a letter between a and z and ends with at. [a-zA-Z]at will match any word that starts with a letter between a and z or A and Z and ends with at.

We can also group our search terms together using the () operator. For example, /(f|c)at/ will match fat and cat since we are saying to find any word starting with f or c and ending with at.

Another special operator is the ^ operator. The ^ operator will match the start of a line. For example, /^The/ will match the first line of the text.
/^I/g would for example not match the It we need to declare /^I/gm to do it for multiline

Likewise we can use the $ operator to match the end of a line. For example, /eat.$/ will match the last line of the text.

TODO:https://www.youtube.com/watch?v=rhzKDrUiJVk&t=637s 13:36 
