---
type: note
created_at: '2026-10-22T02:52:08.829Z'
updated_at: '2026-10-22T02:52:08.829Z'
---
## Problem
Given the root of a binary tree, return the level order traversal of its nodes' values (left-to-right, level-by-level).

**LeetCode**: https://leetcode.com/problems/binary-tree-level-order-traversal/
**Difficulty**: Medium

## Approach
Use a queue for BFS traversal. Process nodes level by level.

## Solution
```python
from collections import deque

def levelOrder(root):
    if not root:
        return []
    result = []
    queue = deque([root])
    while queue:
        level_size = len(queue)
        current_level = []
        for _ in range(level_size):
            node = queue.popleft()
            current_level.append(node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        result.append(current_level)
    return result
```

## Complexity
- **Time**: O(n)
- **Space**: O(w)
