---
type: note
created_at: '2026-10-22T02:53:33.562Z'
updated_at: '2026-10-22T02:53:33.562Z'
---
## Problem
You are climbing a staircase. It takes `n` steps to reach the top. Each time you can climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**LeetCode**: https://leetcode.com/problems/climbing-stairs/
**Difficulty**: Easy

## Approach
DP approach. Each step can be reached from step n-1 or n-2.

## Solution
```python
def climbStairs(n):
    if n <= 2:
        return n
    dp = [0] * (n + 1)
    dp[1], dp[2] = 1, 2
    for i in range(3, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    return dp[n]
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
