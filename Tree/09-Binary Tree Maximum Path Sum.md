---
type: note
created_at: '2026-10-22T02:52:17.289Z'
updated_at: '2026-10-22T02:52:17.289Z'
---
## Problem
A path in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence at most once. Note that the path does not need to pass through the root. Return the maximum path sum of any non-empty path.

**LeetCode**: https://leetcode.com/problems/binary-tree-maximum-path-sum/
**Difficulty**: Hard

## Approach
DFS recursion. Track the maximum gain from each subtree and update the global maximum.

## Solution
```python
def maxPathSum(root):
    max_sum = float('-inf')
    
    def dfs(node):
        nonlocal max_sum
        if not node:
            return 0
        left_max = max(0, dfs(node.left))
        right_max = max(0, dfs(node.right))
        max_sum = max(max_sum, node.val + left_max + right_max)
        return node.val + max(left_max, right_max)
    
    dfs(root)
    return max_sum
```

## Complexity
- **Time**: O(n)
- **Space**: O(h)
