---
type: note
created_at: '2026-10-22T02:52:22.010Z'
updated_at: '2026-10-22T02:52:22.010Z'
---
## Problem
Given a reference of a node in a connected undirected graph, return a deep copy (clone) of the graph.

**LeetCode**: https://leetcode.com/problems/clone-graph/
**Difficulty**: Medium

## Approach
Use DFS with a hash map to track visited nodes and their clones.

## Solution
```python
class Node:
    def __init__(self, val=0, neighbors=None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []

def cloneGraph(node):
    if not node:
        return None
    clones = {}
    def dfs(node):
        if node in clones:
            return clones[node]
        clone = Node(node.val)
        clones[node] = clone
        for neighbor in node.neighbors:
            clone.neighbors.append(dfs(neighbor))
        return clone
    return dfs(node)
```

## Complexity
- **Time**: O(n + e)
- **Space**: O(n)
