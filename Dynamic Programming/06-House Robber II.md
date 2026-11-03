---
type: note
created_at: '2026-10-22T02:53:49.457Z'
updated_at: '2026-10-22T02:53:49.457Z'
---
## Problem
You are a professional robber planning to rob houses along a street where all houses are arranged in a circle. You cannot rob two adjacent houses. Given an integer array `nums` representing the amount of money in each house, return the maximum amount of money you can rob without alerting the police.

**LeetCode**: https://leetcode.com/problems/house-robber-ii/
**Difficulty**: Medium

## Approach
Handle circular constraint by solving two cases: rob excluding last house, rob excluding first house.

## Solution
```python
def rob(nums):
    def rob_linear(houses):
        if not houses:
            return 0
        if len(houses) == 1:
            return houses[0]
        dp = [0] * len(houses)
        dp[0] = houses[0]
        dp[1] = max(houses[0], houses[1])
        for i in range(2, len(houses)):
            dp[i] = max(dp[i-1], dp[i-2] + houses[i])
        return dp[-1]
    
    return max(rob_linear(nums[:-1]), rob_linear(nums[1:]))
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
