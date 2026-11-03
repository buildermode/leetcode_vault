---
type: note
created_at: '2026-10-22T02:52:38.276Z'
updated_at: '2026-10-22T02:52:38.276Z'
---
## Problem
There is a new alien language which uses the latin alphabet. However, the order among letters are unknown to you. You receive a list of non-empty words written in this alien language, where words are sorted in the dictionary order. Derive the order of letters in this alien language.

**LeetCode**: https://leetcode.com/problems/alien-dictionary/
**Difficulty**: Hard

## Approach
Build a graph of character ordering from the word list, then perform topological sort.

## Solution
```python
def alienOrder(words):
    graph = {c: set() for word in words for c in word}
    indegree = {c: 0 for word in words for c in word}
    
    for i in range(len(words) - 1):
        w1, w2 = words[i], words[i + 1]
        for j in range(min(len(w1), len(w2))):
            if w1[j] != w2[j]:
                if w2[j] not in graph[w1[j]]:
                    graph[w1[j]].add(w2[j])
                    indegree[w2[j]] += 1
                break
    
    queue = [c for c in indegree if indegree[c] == 0]
    result = []
    while queue:
        c = queue.pop(0)
        result.append(c)
        for neighbor in graph[c]:
            indegree[neighbor] -= 1
            if indegree[neighbor] == 0:
                queue.append(neighbor)
    
    return ''.join(result) if len(result) == len(graph) else ''
```

## Complexity
- **Time**: O(n * k + c + e)
- **Space**: O(c + e)
