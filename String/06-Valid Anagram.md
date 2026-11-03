---
type: note
created_at: '2026-10-22T02:51:35.501Z'
updated_at: '2026-10-22T02:51:35.501Z'
---
## Problem
Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise. An anagram is a word formed by rearranging the letters of another word.

**LeetCode**: https://leetcode.com/problems/valid-anagram/
**Difficulty**: Easy

## Approach
Count the frequency of characters in both strings and compare.

## Solution
```python
def isAnagram(s, t):
    if len(s) != len(t):
        return False
    char_count = {}
    for char in s:
        char_count[char] = char_count.get(char, 0) + 1
    for char in t:
        if char not in char_count:
            return False
        char_count[char] -= 1
        if char_count[char] < 0:
            return False
    return True
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
