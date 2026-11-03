---
type: note
created_at: '2026-10-22T02:52:00.068Z'
updated_at: '2026-10-22T02:52:00.068Z'
---
## Problem
Given the roots of two binary trees `p` and `q`, write a function to check if they are the same. Two binary trees are considered the same if they are structurally identical and the nodes have the same values.

**LeetCode**: https://leetcode.com/problems/same-tree/
**Difficulty**: Easy

## Approach
Recursively compare nodes from both trees.

## Solution
```python
def isSameTree(p, q):
    if not p and not q:
        return True
    if not p or not q:
        return False
    if p.val != q.val:
        return False
    return isSameTree(p.left, q.left) and isSameTree(p.right, q.right)
```

## Complexity
- **Time**: O(n)
- **Space**: O(h)
