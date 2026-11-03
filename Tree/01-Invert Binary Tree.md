---
type: note
created_at: '2026-10-22T02:51:55.349Z'
updated_at: '2026-10-22T02:51:55.349Z'
---
## Problem
Given the root of a binary tree, invert the tree, and return its root.

**LeetCode**: https://leetcode.com/problems/invert-binary-tree/
**Difficulty**: Easy

## Approach
Recursively swap left and right children for each node.

## Solution
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def invertTree(root):
    if not root:
        return None
    root.left, root.right = root.right, root.left
    invertTree(root.left)
    invertTree(root.right)
    return root
```

## Complexity
- **Time**: O(n)
- **Space**: O(h)
