---
type: note
created_at: '2026-10-22T02:53:46.062Z'
updated_at: '2026-10-22T02:53:46.062Z'
---
## Problem
You are a professional robber planning to rob houses along a street. You cannot rob two adjacent houses. Given an integer array `nums` representing the amount of money in each house, return the maximum amount of money you can rob without alerting the police.

**LeetCode**: https://leetcode.com/problems/house-robber/
**Difficulty**: Medium

## Approach
DP approach. dp[i] is the maximum money robbed up to house i.

## Solution
```python
def rob(nums):
    if not nums:
        return 0
    if len(nums) == 1:
        return nums[0]
    dp = [0] * len(nums)
    dp[0] = nums[0]
    dp[1] = max(nums[0], nums[1])
    for i in range(2, len(nums)):
        dp[i] = max(dp[i-1], dp[i-2] + nums[i])
    return dp[-1]
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
