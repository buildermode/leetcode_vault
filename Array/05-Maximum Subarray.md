---
type: note
created_at: '2026-10-22T02:51:04.231Z'
updated_at: '2026-10-22T02:51:04.231Z'
---
## Problem
Given an integer array `nums`, find the subarray with the largest sum and return the sum. A subarray is a contiguous part of an array.

**LeetCode**: https://leetcode.com/problems/maximum-subarray/
**Difficulty**: Medium

## Approach
Kadane's algorithm: track the maximum sum ending at the current position and the overall maximum.

## Solution
```python
def maxSubArray(nums):
    max_current = max_global = nums[0]
    for num in nums[1:]:
        max_current = max(num, max_current + num)
        max_global = max(max_global, max_current)
    return max_global
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
