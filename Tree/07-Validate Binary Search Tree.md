---
type: note
created_at: '2026-10-22T02:52:11.569Z'
updated_at: '2026-10-22T02:52:11.569Z'
---
## Problem
Given the root of a binary tree, determine if it is a valid binary search tree (BST). A valid BST is defined as follows:
- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree contains only nodes with keys greater than the node's key.

**LeetCode**: https://leetcode.com/problems/validate-binary-search-tree/
**Difficulty**: Medium

## Approach
Use min and max bounds. For each node, verify it's within bounds and recurse on children with updated bounds.

## Solution
```python
def isValidBST(root):
    def validate(node, min_val, max_val):
        if not node:
            return True
        if node.val <= min_val or node.val >= max_val:
            return False
        return validate(node.left, min_val, node.val) and validate(node.right, node.val, max_val)
    
    return validate(root, float('-inf'), float('inf'))
```

## Complexity
- **Time**: O(n)
- **Space**: O(h)
