---
type: note
created_at: '2026-10-22T02:53:39.730Z'
updated_at: '2026-10-22T02:53:39.730Z'
---
## Problem
Given an integer array `nums`, return the length of the longest strictly increasing subsequence.

**LeetCode**: https://leetcode.com/problems/longest-increasing-subsequence/
**Difficulty**: Medium

## Approach
DP approach. dp[i] is the length of the longest increasing subsequence ending at i.

## Solution
```python
def lengthOfLIS(nums):
    if not nums:
        return 0
    dp = [1] * len(nums)
    for i in range(1, len(nums)):
        for j in range(i):
            if nums[j] < nums[i]:
                dp[i] = max(dp[i], dp[j] + 1)
    return max(dp)
```

## Complexity
- **Time**: O(n²)
- **Space**: O(n)
