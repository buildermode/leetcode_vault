---
type: note
created_at: '2026-10-22T02:53:25.878Z'
updated_at: '2026-10-22T02:53:25.878Z'
---
## Problem
Given an integer array `nums` where you are positioned at index 0, return the minimum number of jumps to reach the last index. You can assume you can always reach the last index.

**LeetCode**: https://leetcode.com/problems/jump-game-ii/
**Difficulty**: Medium

## Approach
Greedy approach. Track the furthest position reachable in current jump and the furthest in next jump.

## Solution
```python
def jump(nums):
    jumps = 0
    current_end = 0
    furthest = 0
    for i in range(len(nums) - 1):
        furthest = max(furthest, i + nums[i])
        if i == current_end:
            jumps += 1
            current_end = furthest
    return jumps
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
