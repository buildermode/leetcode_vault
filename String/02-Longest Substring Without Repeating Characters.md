---
type: note
created_at: '2026-10-22T02:51:21.993Z'
updated_at: '2026-10-22T02:51:21.993Z'
---
## Problem
Given a string `s`, find the length of the longest substring without repeating characters.

**LeetCode**: https://leetcode.com/problems/longest-substring-without-repeating-characters/
**Difficulty**: Medium

## Approach
Use a sliding window with a hash map to track character positions. When a repeat is found, move the left pointer.

## Solution
```python
def lengthOfLongestSubstring(s):
    char_map = {}
    max_len = 0
    left = 0
    for right in range(len(s)):
        if s[right] in char_map and char_map[s[right]] >= left:
            left = char_map[s[right]] + 1
        char_map[s[right]] = right
        max_len = max(max_len, right - left + 1)
    return max_len
```

## Complexity
- **Time**: O(n)
- **Space**: O(min(n, m))
