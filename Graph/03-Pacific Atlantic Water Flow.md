---
type: note
created_at: '2026-10-22T02:52:29.704Z'
updated_at: '2026-10-22T02:52:29.704Z'
---
## Problem
Given an m x n matrix of non-negative integers representing the height of each cell, water can flow from a cell to an adjacent cell with height less than or equal to the current cell's height. Find all cells from which water can flow to both the Pacific and Atlantic oceans.

**LeetCode**: https://leetcode.com/problems/pacific-atlantic-water-flow/
**Difficulty**: Medium

## Approach
DFS from ocean borders. Mark cells that can reach Pacific and Atlantic separately, then find intersections.

## Solution
```python
def pacificAtlantic(heights):
    if not heights:
        return []
    rows, cols = len(heights), len(heights[0])
    pacific = set()
    atlantic = set()
    
    def dfs(r, c, ocean):
        if (r, c) in ocean:
            return
        ocean.add((r, c))
        for dr, dc in [(0, 1), (1, 0), (0, -1), (-1, 0)]:
            nr, nc = r + dr, c + dc
            if 0 <= nr < rows and 0 <= nc < cols and heights[nr][nc] >= heights[r][c]:
                dfs(nr, nc, ocean)
    
    for r in range(rows):
        dfs(r, 0, pacific)
        dfs(r, cols - 1, atlantic)
    for c in range(cols):
        dfs(0, c, pacific)
        dfs(rows - 1, c, atlantic)
    
    return list(pacific & atlantic)
```

## Complexity
- **Time**: O(m * n)
- **Space**: O(m * n)
