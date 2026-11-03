---
type: note
created_at: '2026-10-22T02:55:06.084Z'
updated_at: '2026-10-22T02:55:06.084Z'
---
## Problem
Given an array `nums` of size n, return the majority element. The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume the majority element always exists in the array.

**LeetCode**: https://leetcode.com/problems/majority-element/
**Difficulty**: Easy

## Approach
Boyer-Moore voting algorithm. Maintain a candidate and count.

## Solution
```python
def majorityElement(nums):
    count = 0
    candidate = None
    for num in nums:
        if count == 0:
            candidate = num
        count += (1 if num == candidate else -1)
    return candidate
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
