---
type: note
created_at: '2026-10-22T02:54:31.880Z'
updated_at: '2026-10-22T02:54:31.880Z'
---
## Problem
Given two sorted arrays `nums1` and `nums2` of size m and n respectively, return the median of the two sorted arrays. The overall run time complexity should be O(log(min(m, n))).

**LeetCode**: https://leetcode.com/problems/median-of-two-sorted-arrays/
**Difficulty**: Hard

## Approach
Binary search on the smaller array to partition both arrays correctly.

## Solution
```python
def findMedianSortedArrays(nums1, nums2):
    if len(nums1) > len(nums2):
        nums1, nums2 = nums2, nums1
    
    low, high = 0, len(nums1)
    while low <= high:
        cut1 = (low + high) // 2
        cut2 = (len(nums1) + len(nums2) + 1) // 2 - cut1
        
        left1 = float('-inf') if cut1 == 0 else nums1[cut1-1]
        right1 = float('inf') if cut1 == len(nums1) else nums1[cut1]
        left2 = float('-inf') if cut2 == 0 else nums2[cut2-1]
        right2 = float('inf') if cut2 == len(nums2) else nums2[cut2]
        
        if left1 <= right2 and left2 <= right1:
            if (len(nums1) + len(nums2)) % 2 == 0:
                return (max(left1, left2) + min(right1, right2)) / 2
            else:
                return max(left1, left2)
        elif left1 > right2:
            high = cut1 - 1
        else:
            low = cut1 + 1
```

## Complexity
- **Time**: O(log(min(m, n)))
- **Space**: O(1)
