---
type: note
created_at: '2026-10-22T02:52:53.116Z'
updated_at: '2026-10-22T02:52:53.116Z'
---
## Problem
You are given a list of airline tickets where tickets[i] = [fromi, toi]. Reconstruct the itinerary in order starting from "JFK". All other tickets' starting city is guaranteed to be in the list of tickets, so the itinerary always exists and you may assume all tickets form at least one valid itinerary.

**LeetCode**: https://leetcode.com/problems/reconstruct-itinerary/
**Difficulty**: Hard

## Approach
Use DFS with a graph of routes. Use Hierholzer's algorithm to find an Eulerian path.

## Solution
```python
def findItinerary(tickets):
    from collections import defaultdict
    graph = defaultdict(list)
    for src, dst in tickets:
        graph[src].append(dst)
    for key in graph:
        graph[key].sort()
    
    result = []
    stack = ["JFK"]
    
    while stack:
        curr = stack[-1]
        if graph[curr]:
            next_airport = graph[curr].pop(0)
            stack.append(next_airport)
        else:
            result.append(stack.pop())
    
    return result[::-1]
```

## Complexity
- **Time**: O(n log n)
- **Space**: O(n)
