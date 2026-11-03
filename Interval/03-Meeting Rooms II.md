---
type: note
created_at: '2026-10-22T02:53:16.329Z'
updated_at: '2026-10-22T02:53:16.329Z'
---
## Problem
Given an array of meeting intervals intervals where intervals[i] = [starti, endi], return the minimum number of conference rooms required.

**LeetCode**: https://leetcode.com/problems/meeting-rooms-ii/
**Difficulty**: Medium

## Approach
Use a heap to track the earliest end time. For each meeting, check if we can reuse a room.

## Solution
```python
import heapq

def minMeetingRooms(intervals):
    if not intervals:
        return 0
    intervals.sort()
    heap = [intervals[0][1]]
    for start, end in intervals[1:]:
        if start >= heap[0]:
            heapq.heappushpop(heap, end)
        else:
            heapq.heappush(heap, end)
    return len(heap)
```

## Complexity
- **Time**: O(n log n)
- **Space**: O(n)
