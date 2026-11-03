---
type: note
created_at: '2026-10-22T02:52:25.606Z'
updated_at: '2026-10-22T02:52:25.606Z'
---
## Problem
There are a total of `numCourses` courses you have to take, labeled from 0 to numCourses - 1. You are given an array `prerequisites` where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai. Return `true` if you can finish all courses, otherwise return `false`.

**LeetCode**: https://leetcode.com/problems/course-schedule/
**Difficulty**: Medium

## Approach
Detect cycle using DFS. If a cycle exists, courses can't be completed.

## Solution
```python
def canFinish(numCourses, prerequisites):
    graph = [[] for _ in range(numCourses)]
    for course, prereq in prerequisites:
        graph[prereq].append(course)
    
    visited = [0] * numCourses  # 0: unvisited, 1: visiting, 2: visited
    
    def hasCycle(course):
        if visited[course] == 1:
            return True
        if visited[course] == 2:
            return False
        visited[course] = 1
        for neighbor in graph[course]:
            if hasCycle(neighbor):
                return True
        visited[course] = 2
        return False
    
    for i in range(numCourses):
        if hasCycle(i):
            return False
    return True
```

## Complexity
- **Time**: O(n + e)
- **Space**: O(n)
