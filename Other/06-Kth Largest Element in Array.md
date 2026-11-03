---
type: note
created_at: '2026-10-22T02:54:48.054Z'
updated_at: '2026-10-22T02:54:48.054Z'
---
## Problem
Given an integer array `nums` and an integer `k`, return the kth largest element in the array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

**LeetCode**: https://leetcode.com/problems/kth-largest-element-in-an-array/
**Difficulty**: Medium

## Approach
Use a min heap of size k to track the k largest elements.

## Solution
```python
import heapq

def findKthLargest(nums, k):
    heap = []
    for num in nums:
        heapq.heappush(heap, num)
        if len(heap) > k:
            heapq.heappop(heap)
    return heap[0]
```

## Complexity
- **Time**: O(n log k)
- **Space**: O(k)
