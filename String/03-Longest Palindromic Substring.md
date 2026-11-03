---
type: note
created_at: '2026-10-22T02:51:25.142Z'
updated_at: '2026-10-22T02:51:25.142Z'
---
## Problem
Given a string `s`, return the longest palindromic substring in `s`.

**LeetCode**: https://leetcode.com/problems/longest-palindromic-substring/
**Difficulty**: Medium

## Approach
Expand around center approach. For each possible center, expand outward and track the longest palindrome found.

## Solution
```python
def longestPalindrome(s):
    if not s:
        return ""
    def expand_around_center(left, right):
        while left >= 0 and right < len(s) and s[left] == s[right]:
            left -= 1
            right += 1
        return s[left + 1:right]
    
    longest = ""
    for i in range(len(s)):
        pal1 = expand_around_center(i, i)
        pal2 = expand_around_center(i, i + 1)
        longest = max(longest, pal1, pal2, key=len)
    return longest
```

## Complexity
- **Time**: O(n²)
- **Space**: O(1)
