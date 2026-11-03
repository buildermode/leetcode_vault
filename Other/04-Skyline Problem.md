---
type: note
created_at: '2026-10-22T02:54:40.434Z'
updated_at: '2026-10-22T02:54:40.434Z'
---
## Problem
A city's skyline is the outer contour of the silhouette formed by all the buildings in that city when viewed from a distance. Given the locations and heights of all the buildings, return the skyline formed by these buildings collectively as a list of key points.

**LeetCode**: https://leetcode.com/problems/the-skyline-problem/
**Difficulty**: Hard

## Approach
Use a heap with events (building start/end) and track active building heights.

## Solution
```python
import heapq
from collections import defaultdict

def getSkyline(buildings):
    events = []
    for left, right, h in buildings:
        events.append((left, 0, h))  # Start
        events.append((right, 1, h))  # End
    events.sort()
    
    result = []
    from sortedcontainers import SortedDict
    heights = SortedDict({0: 1})
    
    for x, t, h in events:
        if t == 0:
            heights[h] = heights.get(h, 0) + 1
        else:
            heights[h] -= 1
            if heights[h] == 0:
                del heights[h]
        
        max_h = heights.peekitem(-1)[0]
        if not result or result[-1][1] != max_h:
            result.append((x, max_h))
    
    return result
```

## Complexity
- **Time**: O(n log n)
- **Space**: O(n)
