---
type: note
created_at: '2026-10-22T02:52:14.268Z'
updated_at: '2026-10-22T02:52:14.268Z'
---
## Problem
Given the root of a binary tree and an integer targetSum, return `true` if the tree has a root-to-leaf path such that adding up all the values along the path equals targetSum.

**LeetCode**: https://leetcode.com/problems/path-sum/
**Difficulty**: Easy

## Approach
DFS recursion. At each leaf, check if the cumulative sum equals the target.

## Solution
```python
def hasPathSum(root, targetSum):
    def dfs(node, current_sum):
        if not node:
            return False
        current_sum += node.val
        if not node.left and not node.right:
            return current_sum == targetSum
        return dfs(node.left, current_sum) or dfs(node.right, current_sum)
    
    return dfs(root, 0)
```

## Complexity
- **Time**: O(n)
- **Space**: O(h)
