---
type: note
created_at: '2026-10-22T02:52:57.046Z'
updated_at: '2026-10-22T02:52:57.046Z'
---
## Problem
Given an m x n board containing 'X' and 'O', capture all regions that are 4-directionally surrounded by 'X'. A region is captured by flipping all 'O's into 'X's in that surrounded region.

**LeetCode**: https://leetcode.com/problems/surrounded-regions/
**Difficulty**: Medium

## Approach
DFS from borders to mark all O's connected to border. Remaining O's are surrounded.

## Solution
```python
def solve(board):
    if not board:
        return
    rows, cols = len(board), len(board[0])
    
    def dfs(r, c):
        if r < 0 or r >= rows or c < 0 or c >= cols or board[r][c] != 'O':
            return
        board[r][c] = 'T'
        dfs(r + 1, c)
        dfs(r - 1, c)
        dfs(r, c + 1)
        dfs(r, c - 1)
    
    for r in range(rows):
        dfs(r, 0)
        dfs(r, cols - 1)
    for c in range(cols):
        dfs(0, c)
        dfs(rows - 1, c)
    
    for r in range(rows):
        for c in range(cols):
            if board[r][c] == 'T':
                board[r][c] = 'O'
            else:
                board[r][c] = 'X'
```

## Complexity
- **Time**: O(m * n)
- **Space**: O(m * n)
