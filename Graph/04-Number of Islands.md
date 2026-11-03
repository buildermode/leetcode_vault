---
type: note
created_at: '2026-10-22T02:52:33.555Z'
updated_at: '2026-10-22T02:52:33.555Z'
---
## Problem
Given an m x n 2D binary grid `grid` which represents a map of '1's (land) and '0's (water), return the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically.

**LeetCode**: https://leetcode.com/problems/number-of-islands/
**Difficulty**: Medium

## Approach
DFS to explore each island and mark all connected lands as visited.

## Solution
```python
def numIslands(grid):
    if not grid:
        return 0
    rows, cols = len(grid), len(grid[0])
    count = 0
    
    def dfs(r, c):
        if r < 0 or r >= rows or c < 0 or c >= cols or grid[r][c] == '0':
            return
        grid[r][c] = '0'
        dfs(r + 1, c)
        dfs(r - 1, c)
        dfs(r, c + 1)
        dfs(r, c - 1)
    
    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == '1':
                count += 1
                dfs(r, c)
    return count
```

## Complexity
- **Time**: O(m * n)
- **Space**: O(m * n)
