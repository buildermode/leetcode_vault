---
type: note
created_at: '2026-10-22T02:54:44.524Z'
updated_at: '2026-10-22T02:54:44.524Z'
---
## Problem
Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer. Design an algorithm to serialize and deserialize a binary tree.

**LeetCode**: https://leetcode.com/problems/serialize-and-deserialize-binary-tree/
**Difficulty**: Hard

## Approach
Use preorder traversal with markers for null nodes.

## Solution
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Codec:
    def serialize(self, root):
        def dfs(node):
            if not node:
                return ['#']
            return [str(node.val)] + dfs(node.left) + dfs(node.right)
        return ','.join(dfs(root))
    
    def deserialize(self, data):
        def dfs(nodes):
            val = next(nodes)
            if val == '#':
                return None
            node = TreeNode(int(val))
            node.left = dfs(nodes)
            node.right = dfs(nodes)
            return node
        nodes = iter(data.split(','))
        return dfs(nodes)
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
