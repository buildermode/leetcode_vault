---
type: note
created_at: '2026-10-22T02:51:57.730Z'
updated_at: '2026-10-22T02:51:57.730Z'
---
## Problem
Given the root of a binary tree, return its maximum depth. The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

**LeetCode**: https://leetcode.com/problems/maximum-depth-of-binary-tree/
**Difficulty**: Easy

## Approach
Recursively find the maximum depth of left and right subtrees and take the maximum.

## Solution
```python
def maxDepth(root):
    if not root:
        return 0
    return 1 + max(maxDepth(root.left), maxDepth(root.right))
```

## Complexity
- **Time**: O(n)
- **Space**: O(h)
