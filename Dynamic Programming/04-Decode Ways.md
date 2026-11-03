---
type: note
created_at: '2026-10-22T02:53:43.096Z'
updated_at: '2026-10-22T02:53:43.096Z'
---
## Problem
A message containing letters from A-Z can be encoded into numbers using the following mapping: 'A' -> "1", 'B' -> "2", ..., 'Z' -> "26". Given a string `s` containing only digits, return the number of ways to decode it.

**LeetCode**: https://leetcode.com/problems/decode-ways/
**Difficulty**: Medium

## Approach
DP approach. dp[i] is the number of ways to decode the string up to index i.

## Solution
```python
def numDecodings(s):
    if not s or s[0] == '0':
        return 0
    dp = [0] * (len(s) + 1)
    dp[0] = dp[1] = 1
    for i in range(2, len(s) + 1):
        if s[i-1] != '0':
            dp[i] += dp[i-1]
        if 10 <= int(s[i-2:i]) <= 26:
            dp[i] += dp[i-2]
    return dp[len(s)]
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
