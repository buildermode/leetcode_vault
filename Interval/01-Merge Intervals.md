---
type: note
created_at: '2026-10-22T02:53:10.193Z'
updated_at: '2026-10-22T02:53:10.193Z'
---
## Problem
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals.

**LeetCode**: https://leetcode.com/problems/merge-intervals/
**Difficulty**: Medium

## Approach
Sort by start time, then merge overlapping intervals.

## Solution
```python
def merge(intervals):
    if not intervals:
        return []
    intervals.sort()
    merged = [intervals[0]]
    for current in intervals[1:]:
        last = merged[-1]
        if current[0] <= last[1]:
            merged[-1] = [last[0], max(last[1], current[1])]
        else:
            merged.append(current)
    return merged
```

## Complexity
- **Time**: O(n log n)
- **Space**: O(1)
