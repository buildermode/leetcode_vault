---
type: note
created_at: '2026-10-22T02:51:11.037Z'
updated_at: '2026-10-22T02:51:11.037Z'
---
## Problem
There is an integer array `nums` sorted in ascending order that is rotated at some unknown pivot. Find the target value. Return its index if found, otherwise return -1. You must solve this with O(log n) runtime complexity.

**LeetCode**: https://leetcode.com/problems/search-in-rotated-sorted-array/
**Difficulty**: Medium

## Approach
Use binary search. Identify which half is sorted, then determine if the target is in that half or the other half.

## Solution
```python
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        if nums[left] <= nums[mid]:  # Left half is sorted
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:  # Right half is sorted
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    return -1
```

## Complexity
- **Time**: O(log n)
- **Space**: O(1)
