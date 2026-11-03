---
type: note
created_at: '2026-10-22T02:52:03.129Z'
updated_at: '2026-10-22T02:52:03.129Z'
---
## Problem
Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot`, and `false` otherwise.

**LeetCode**: https://leetcode.com/problems/subtree-of-another-tree/
**Difficulty**: Easy

## Approach
For each node in the main tree, check if the subtree rooted at that node is the same as subRoot.

## Solution
```python
def isSubtree(root, subRoot):
    def isSameTree(p, q):
        if not p and not q:
            return True
        if not p or not q or p.val != q.val:
            return False
        return isSameTree(p.left, q.left) and isSameTree(p.right, q.right)
    
    if not root:
        return False
    if isSameTree(root, subRoot):
        return True
    return isSubtree(root.left, subRoot) or isSubtree(root.right, subRoot)
```

## Complexity
- **Time**: O(n * m)
- **Space**: O(h)
