---
type: note
created_at: '2026-10-22T02:52:45.272Z'
updated_at: '2026-10-22T02:52:45.272Z'
---
## Problem
You have a graph of n nodes. You are given an integer n and an array edges where edges[i] = [ai, bi] indicates that there is an edge between ai and bi in the graph. Return the number of connected components in the graph.

**LeetCode**: https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/
**Difficulty**: Medium

## Approach
DFS or Union-Find. Count the number of disconnected components.

## Solution
```python
def countComponents(n, edges):
    graph = [[] for _ in range(n)]
    for u, v in edges:
        graph[u].append(v)
        graph[v].append(u)
    
    visited = set()
    count = 0
    
    def dfs(node):
        visited.add(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                dfs(neighbor)
    
    for i in range(n):
        if i not in visited:
            dfs(i)
            count += 1
    return count
```

## Complexity
- **Time**: O(n + e)
- **Space**: O(n)
