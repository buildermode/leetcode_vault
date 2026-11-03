---
type: note
created_at: '2026-10-22T02:53:55.297Z'
updated_at: '2026-10-22T02:53:55.297Z'
---
## Problem
Given a non-empty array `nums` containing only positive integers, determine if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.

**LeetCode**: https://leetcode.com/problems/partition-equal-subset-sum/
**Difficulty**: Medium

## Approach
0/1 Knapsack problem. Check if we can achieve sum/2.

## Solution
```python
def canPartition(nums):
    total = sum(nums)
    if total % 2 != 0:
        return False
    target = total // 2
    dp = [False] * (target + 1)
    dp[0] = True
    for num in nums:
        for i in range(target, num - 1, -1):
            dp[i] = dp[i] or dp[i - num]
    return dp[target]
```

## Complexity
- **Time**: O(n * target)
- **Space**: O(target)
