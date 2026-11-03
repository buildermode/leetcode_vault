---
type: note
created_at: '2026-10-22T02:51:07.756Z'
updated_at: '2026-10-22T02:51:07.756Z'
---
## Problem
Given an integer array `nums`, find a subarray that has the largest product and return the product.

**LeetCode**: https://leetcode.com/problems/maximum-product-subarray/
**Difficulty**: Medium

## Approach
Track both maximum and minimum products at each position (negative numbers can flip min to max). Update globals accordingly.

## Solution
```python
def maxProduct(nums):
    max_prod = min_prod = result = nums[0]
    for num in nums[1:]:
        max_prod, min_prod = max(num, max_prod * num, min_prod * num), min(num, max_prod * num, min_prod * num)
        result = max(result, max_prod)
    return result
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
