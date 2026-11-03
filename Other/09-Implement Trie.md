---
type: note
created_at: '2026-10-22T02:54:57.781Z'
updated_at: '2026-10-22T02:54:57.781Z'
---
## Problem
A trie (pronounced as "try") or prefix tree is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. Implement the Trie class with insert, search, and startsWith methods.

**LeetCode**: https://leetcode.com/problems/implement-trie-prefix-tree/
**Difficulty**: Medium

## Approach
Use a nested dictionary structure where each node has children and an end marker.

## Solution
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end = True
    
    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end
    
    def startsWith(self, prefix):
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True
```

## Complexity
- **Insert/Search/StartsWith**: O(m) where m is length of word
- **Space**: O(ALPHABET_SIZE * m * n)
