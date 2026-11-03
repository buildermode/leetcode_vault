---
type: note
created_at: '2026-10-22T02:51:32.218Z'
updated_at: '2026-10-22T02:51:32.218Z'
---
## Problem
Given two strings `s` and `t` of lengths m and n respectively, return the minimum window substring of `s` such that every character in `t` is included in the window. If there is no such window, return an empty string.

**LeetCode**: https://leetcode.com/problems/minimum-window-substring/
**Difficulty**: Hard

## Approach
Use a sliding window with hash maps to track character frequencies. Expand right pointer and contract left when all characters are in window.

## Solution
```python
def minWindow(s, t):
    if not s or not t:
        return ""
    dict_t = {}
    for char in t:
        dict_t[char] = dict_t.get(char, 0) + 1
    
    required = len(dict_t)
    window_counts = {}
    formed = 0
    left = 0
    ans = float("inf"), None, None
    
    for right in range(len(s)):
        window_counts[s[right]] = window_counts.get(s[right], 0) + 1
        if s[right] in dict_t and window_counts[s[right]] == dict_t[s[right]]:
            formed += 1
        while left <= right and formed == required:
            if right - left + 1 < ans[0]:
                ans = (right - left + 1, left, right)
            window_counts[s[left]] -= 1
            if s[left] in dict_t and window_counts[s[left]] < dict_t[s[left]]:
                formed -= 1
            left += 1
    return "" if ans[0] == float("inf") else s[ans[1]:ans[2] + 1]
```

## Complexity
- **Time**: O(n + m)
- **Space**: O(n + m)
