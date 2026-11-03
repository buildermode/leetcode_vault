---
type: note
created_at: '2026-10-22T02:53:06.020Z'
updated_at: '2026-10-22T02:53:06.020Z'
---
## Problem
There are n servers numbered from 0 to n - 1 connected by undirected server-to-server connections forming a network where connections[i] = [ai, bi] represents a connection between servers ai and bi. Any server can reach any other server directly or indirectly through the network. A critical connection is a connection that, if removed, will make some server unable to reach some other server. Return all critical connections in the network in any order.

**LeetCode**: https://leetcode.com/problems/critical-connections-in-a-network/
**Difficulty**: Hard

## Approach
Use Tarjan's algorithm to find bridges in the graph.

## Solution
```python
def criticalConnections(n, connections):
    graph = [[] for _ in range(n)]
    for u, v in connections:
        graph[u].append(v)
        graph[v].append(u)
    
    disc = [-1] * n
    low = [-1] * n
    result = []
    time = [0]
    
    def dfs(u, p):
        disc[u] = low[u] = time[0]
        time[0] += 1
        for v in graph[u]:
            if disc[v] == -1:
                dfs(v, u)
                low[u] = min(low[u], low[v])
                if low[v] > disc[u]:
                    result.append([u, v])
            elif v != p:
                low[u] = min(low[u], disc[v])
    
    dfs(0, -1)
    return result
```

## Complexity
- **Time**: O(n + e)
- **Space**: O(n + e)
