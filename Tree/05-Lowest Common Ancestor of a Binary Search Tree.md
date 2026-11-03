---
type: note
created_at: '2026-10-22T02:52:05.993Z'
updated_at: '2026-10-22T02:52:05.993Z'
---
## Problem
Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

**LeetCode**: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/
**Difficulty**: Medium

## Approach
Use BST properties. If both nodes are less than root, go left. If both are greater, go right. Otherwise, root is the LCA.

## Solution
```python
def lowestCommonAncestor(root, p, q):
    while root:
        if p.val < root.val and q.val < root.val:
            root = root.left
        elif p.val > root.val and q.val > root.val:
            root = root.right
        else:
            return root
```

## Complexity
- **Time**: O(log n) average, O(n) worst
- **Space**: O(1)
