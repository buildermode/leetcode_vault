---
type: note
created_at: '2026-10-22T02:53:13.419Z'
updated_at: '2026-10-22T02:53:13.419Z'
---
## Problem
You are given an array of non-overlapping intervals and a new interval. Insert the new interval into the array such that the new interval does not overlap with any of the existing intervals. If necessary, merge intervals.

**LeetCode**: https://leetcode.com/problems/insert-interval/
**Difficulty**: Medium

## Approach
Collect non-overlapping intervals before and after the new interval, then merge.

## Solution
```python
def insert(intervals, newInterval):
    result = []
    i = 0
    while i < len(intervals) and intervals[i][1] < newInterval[0]:
        result.append(intervals[i])
        i += 1
    while i < len(intervals) and intervals[i][0] <= newInterval[1]:
        newInterval = [min(newInterval[0], intervals[i][0]), max(newInterval[1], intervals[i][1])]
        i += 1
    result.append(newInterval)
    while i < len(intervals):
        result.append(intervals[i])
        i += 1
    return result
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
