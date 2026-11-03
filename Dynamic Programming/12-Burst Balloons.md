---
type: note
created_at: '2026-10-22T02:54:09.990Z'
updated_at: '2026-10-22T02:54:09.990Z'
---
## Problem
You are given n balloons, indexed from 0 to n - 1. Each balloon is painted with a number on it. You are asked to burst all the balloons. If you burst balloon i, you will get nums[left] * nums[i] * nums[right] coins. After the burst, the left and right then become adjacent. Return the maximum coins you can collect by bursting the balloons wisely.

**LeetCode**: https://leetcode.com/problems/burst-balloons/
**Difficulty**: Hard

## Approach
DP with interval approach. Process balloons in reverse order of bursting.

## Solution
```python
def maxCoins(nums):
    nums = [1] + [x for x in nums if x > 0] + [1]
    n = len(nums)
    dp = [[0] * n for _ in range(n)]
    
    for length in range(2, n):
        for left in range(n - length):
            right = left + length
            for k in range(left + 1, right):
                dp[left][right] = max(
                    dp[left][right],
                    dp[left][k] + dp[k][right] + nums[left] * nums[k] * nums[right]
                )
    return dp[0][-1]
```

## Complexity
- **Time**: O(n³)
- **Space**: O(n²)
