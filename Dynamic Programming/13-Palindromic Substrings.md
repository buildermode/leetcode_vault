---
type: note
created_at: '2026-10-22T02:54:13.712Z'
updated_at: '2026-10-22T02:54:13.712Z'
---
## Problem
Given a string `s`, return the number of palindromic substrings in it. A string is palindromic when it reads the same backward as forward.

**LeetCode**: https://leetcode.com/problems/palindromic-substrings/
**Difficulty**: Medium

## Approach
DP approach. dp[i][j] is true if s[i:j+1] is a palindrome.

## Solution
```python
def countSubstrings(s):
    n = len(s)
    dp = [[False] * n for _ in range(n)]
    count = 0
    
    for i in range(n):
        dp[i][i] = True
        count += 1
    
    for length in range(2, n + 1):
        for i in range(n - length + 1):
            j = i + length - 1
            if s[i] == s[j]:
                if length == 2 or dp[i+1][j-1]:
                    dp[i][j] = True
                    count += 1
    return count
```

## Complexity
- **Time**: O(n²)
- **Space**: O(n²)
