---
type: note
created_at: '2026-10-22T02:54:54.279Z'
updated_at: '2026-10-22T02:54:54.279Z'
---
## Problem
Given an integer array `nums` and an integer `k`, return the k most frequent elements. You may return the answer in any order.

**LeetCode**: https://leetcode.com/problems/top-k-frequent-elements/
**Difficulty**: Medium

## Approach
Count frequencies and use a min heap of size k.

## Solution
```python
import heapq
from collections import Counter

def topKFrequent(nums, k):
    count = Counter(nums)
    heap = []
    for num, freq in count.items():
        heapq.heappush(heap, (freq, num))
        if len(heap) > k:
            heapq.heappop(heap)
    return [num for freq, num in heap]
```

## Complexity
- **Time**: O(n log k)
- **Space**: O(k)
