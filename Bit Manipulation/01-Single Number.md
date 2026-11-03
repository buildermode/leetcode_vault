---
type: note
created_at: '2026-10-22T02:54:17.527Z'
updated_at: '2026-10-22T02:54:17.527Z'
---
## Problem
Given a non-empty array of integers `nums`, every element appears twice except for one element that appears once. Find that single element in O(n) time without using extra space.

**LeetCode**: https://leetcode.com/problems/single-number/
**Difficulty**: Easy

## Approach
XOR operation. a ^ a = 0 and a ^ 0 = a, so XORing all elements gives the single number.

## Solution
```python
def singleNumber(nums):
    result = 0
    for num in nums:
        result ^= num
    return result
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
