---
type: note
created_at: '2026-10-22T02:50:57.648Z'
updated_at: '2026-10-22T02:50:57.648Z'
---
## Problem
Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

**LeetCode**: https://leetcode.com/problems/contains-duplicate/
**Difficulty**: Easy

## Approach
Use a hash set to track seen numbers. Return true if we encounter a duplicate.

## Solution
```python
def containsDuplicate(nums):
    seen = set()
    for num in nums:
        if num in seen:
            return True
        seen.add(num)
    return False
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
