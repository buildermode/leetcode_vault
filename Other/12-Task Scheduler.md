---
type: note
created_at: '2026-10-22T02:55:10.388Z'
updated_at: '2026-10-22T02:55:10.388Z'
---
## Problem
You are given a list of non-preemptive tasks and a certain number of CPU cores. You need to schedule the tasks efficiently. Given tasks as characters and a cooldown time n, the same task cannot be executed consecutively. Find the minimum time units needed to complete all tasks.

**LeetCode**: https://leetcode.com/problems/task-scheduler/
**Difficulty**: Medium

## Approach
Use a max heap and simulate the scheduling process.

## Solution
```python
from collections import Counter
import heapq

def leastInterval(tasks, n):
    task_counts = Counter(tasks)
    max_heap = [-count for count in task_counts.values()]
    heapq.heapify(max_heap)
    
    time = 0
    while max_heap:
        temp = []
        for _ in range(n + 1):
            if max_heap:
                count = heapq.heappop(max_heap)
                if count < -1:
                    temp.append(count + 1)
            time += 1
            if not max_heap and not temp:
                break
        for count in temp:
            heapq.heappush(max_heap, count)
    
    return time
```

## Complexity
- **Time**: O(n log k) where k is number of unique tasks
- **Space**: O(k)
