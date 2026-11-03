---
type: note
created_at: '2026-10-22T02:54:36.151Z'
updated_at: '2026-10-22T02:54:36.151Z'
---
## Problem
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

**LeetCode**: https://leetcode.com/problems/trapping-rain-water/
**Difficulty**: Hard

## Approach
Use two pointers to track maximum heights from left and right. Calculate water at each position.

## Solution
```python
def trap(height):
    if not height:
        return 0
    left, right = 0, len(height) - 1
    max_left, max_right = 0, 0
    water = 0
    
    while left < right:
        if height[left] < height[right]:
            if height[left] >= max_left:
                max_left = height[left]
            else:
                water += max_left - height[left]
            left += 1
        else:
            if height[right] >= max_right:
                max_right = height[right]
            else:
                water += max_right - height[right]
            right -= 1
    return water
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
