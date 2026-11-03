---
type: note
created_at: '2026-10-22T02:54:23.685Z'
updated_at: '2026-10-22T02:54:23.685Z'
---
## Problem
Given an array `nums` containing n distinct numbers taken from the range [0, n], return the only number in the range that is missing from the array.

**LeetCode**: https://leetcode.com/problems/missing-number/
**Difficulty**: Easy

## Approach
Use XOR or mathematical approach. XOR all numbers from 0 to n with all elements in array.

## Solution
```python
def missingNumber(nums):
    # XOR approach
    result = 0
    for i in range(len(nums) + 1):
        result ^= i
    for num in nums:
        result ^= num
    return result

# Or mathematical approach
def missingNumber(nums):
    n = len(nums)
    expected_sum = n * (n + 1) // 2
    actual_sum = sum(nums)
    return expected_sum - actual_sum
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
