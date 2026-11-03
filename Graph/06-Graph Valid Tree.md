---
type: note
created_at: '2026-10-22T02:52:42.023Z'
updated_at: '2026-10-22T02:52:42.023Z'
---
## Problem
Given n nodes labeled from 0 to n - 1 and a list of undirected edges (each edge is a pair of nodes), write a function to check whether these edges make up a valid tree.

**LeetCode**: https://leetcode.com/problems/graph-valid-tree/
**Difficulty**: Medium

## Approach
A valid tree has n nodes and n-1 edges with no cycles. Use DFS to check connectivity and cycle.

## Solution
```python
def validTree(n, edges):
    if len(edges) != n - 1:
        return False
    
    graph = [[] for _ in range(n)]
    for u, v in edges:
        graph[u].append(v)
        graph[v].append(u)
    
    visited = set()
    
    def dfs(node, parent):
        visited.add(node)
        for neighbor in graph[node]:
            if neighbor == parent:
                continue
            if neighbor in visited:
                return False
            if not dfs(neighbor, node):
                return False
        return True
    
    return dfs(0, -1) and len(visited) == n
```

## Complexity
- **Time**: O(n + e)
- **Space**: O(n)
