---
type: note
created_at: '2026-10-22T02:51:00.811Z'
updated_at: '2026-10-22T02:51:00.811Z'
---
## Problem
Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all elements of `nums` except `nums[i]`. You must write an algorithm that runs in O(n) time and uses O(1) space (excluding the output array).

**LeetCode**: https://leetcode.com/problems/product-of-array-except-self/
**Difficulty**: Medium

## Approach
Use prefix and suffix products. For each position, multiply the product of all elements before it with the product of all elements after it.

## Solution
```python
def productExceptSelf(nums):
    n = len(nums)
    answer = [1] * n
    
    # Prefix products
    prefix = 1
    for i in range(n):
        answer[i] = prefix
        prefix *= nums[i]
    
    # Suffix products
    suffix = 1
    for i in range(n - 1, -1, -1):
        answer[i] *= suffix
        suffix *= nums[i]
    
    return answer
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
