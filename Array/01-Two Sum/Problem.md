---
type: note
created_at: '2026-10-22T02:50:51.905Z'
updated_at: '2026-10-22T02:50:51.905Z'
---
## Problem
Given an array of integers `nums` and an integer `target`, return the indices of the two numbers that add up to `target`. Each input has exactly one solution, and the same element cannot be used twice.

**LeetCode**: https://leetcode.com/problems/two-sum/
**Difficulty**: Easy

## Approach
Use a hash map to store numbers and their indices. Iterate through the array, and for each number, check if `target - num` exists in the map.

## Solution
```python
def twoSum(nums, target):
    map = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in map:
            return [map[complement], i]
        map[num] = i
    return []
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
