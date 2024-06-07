---
id: Tries
aliases: []
tags: []
---

# Tries

If it's not a priority queue, it's a Trie.

They are pronounced like Tree (dubbed from "Re'trie'val Tree"). 

The easiest way to visualize a trie is to think of auto-complete. 
- If I type "a" what search should be given back
- ***These retrerivals can occur in 0(1) time given the keys have some finite length***

## English Language Tree
Consider we wanted to make a spell checker and wanted to store the following words:
The structure would look like this:
![tries000.png](assets/imgs/tries000.png)

## Insertion Psudo Code
Insertion(str)
    curr = head
    for c in str:
        if curr[c]:
            curr = curr[c]
        else:
            node = create_node()
            curr = node
            curr.isWord = True
