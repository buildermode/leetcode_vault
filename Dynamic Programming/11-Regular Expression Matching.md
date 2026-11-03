---
type: note
created_at: '2026-10-22T02:54:05.639Z'
updated_at: '2026-10-22T02:54:05.639Z'
---
## Problem
Given an input string `s` and a pattern `p`, implement regular expression matching with support for '.' and '*' where:
- '.' matches any single character.
- '*' matches zero or more of the preceding element.

**LeetCode**: https://leetcode.com/problems/regular-expression-matching/
**Difficulty**: Hard

## Approach
2D DP. dp[i][j] is true if s[0:i] matches p[0:j].

## Solution
```python
def isMatch(s, p):
    m, n = len(s), len(p)
    dp = [[False] * (n + 1) for _ in range(m + 1)]
    dp[0][0] = True
    for j in range(2, n + 1):
        if p[j-1] == '*':
            dp[0][j] = dp[0][j-2]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if p[j-1] == '*':
                dp[i][j] = dp[i][j-2] or (dp[i-1][j] and (s[i-1] == p[j-2] or p[j-2] == '.'))
            else:
                dp[i][j] = dp[i-1][j-1] and (s[i-1] == p[j-1] or p[j-1] == '.')
    return dp[m][n]
```

## Complexity
- **Time**: O(m * n)
- **Space**: O(m * n)
