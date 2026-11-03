---
type: note
created_at: '2026-10-22T02:53:19.107Z'
updated_at: '2026-10-22T02:53:19.107Z'
---
## Problem
Given an array of intervals intervals where intervals[i] = [starti, endi], return the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.

**LeetCode**: https://leetcode.com/problems/non-overlapping-intervals/
**Difficulty**: Medium

## Approach
Greedy approach. Sort by end time and keep intervals that don't overlap.

## Solution
```python
def eraseOverlapIntervals(intervals):
    if not intervals:
        return 0
    intervals.sort(key=lambda x: x[1])
    end = intervals[0][1]
    count = 0
    for i in range(1, len(intervals)):
        if intervals[i][0] < end:
            count += 1
        else:
            end = intervals[i][1]
    return count
```

## Complexity
- **Time**: O(n log n)
- **Space**: O(1)
