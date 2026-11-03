---
type: note
created_at: '2026-10-22T02:53:22.988Z'
updated_at: '2026-10-22T02:53:22.988Z'
---
## Problem
You are given an integer array `nums` where you are initially positioned at the array's first index. Each element in the array represents your maximum jump length at that position. Determine if you can reach the last index.

**LeetCode**: https://leetcode.com/problems/jump-game/
**Difficulty**: Medium

## Approach
Keep track of the furthest position reachable. If at any point current position exceeds it, return false.

## Solution
```python
def canJump(nums):
    max_reach = 0
    for i in range(len(nums)):
        if i > max_reach:
            return False
        max_reach = max(max_reach, i + nums[i])
        if max_reach >= len(nums) - 1:
            return True
    return False
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
