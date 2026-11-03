---
type: note
created_at: '2026-10-22T02:51:28.018Z'
updated_at: '2026-10-22T02:51:28.018Z'
---
## Problem
Given an array of strings `strs`, group the anagrams together. You can return the answer in any order.

**LeetCode**: https://leetcode.com/problems/group-anagrams/
**Difficulty**: Medium

## Approach
Use a hash map where the key is the sorted string and the value is the list of anagrams.

## Solution
```python
def groupAnagrams(strs):
    anagram_map = {}
    for s in strs:
        key = ''.join(sorted(s))
        if key not in anagram_map:
            anagram_map[key] = []
        anagram_map[key].append(s)
    return list(anagram_map.values())
```

## Complexity
- **Time**: O(n * k log k) where k is the length of the longest string
- **Space**: O(n * k)
