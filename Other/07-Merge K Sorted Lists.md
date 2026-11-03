---
type: note
created_at: '2026-10-22T02:54:51.506Z'
updated_at: '2026-10-22T02:54:51.506Z'
---
## Problem
You are given an array of k linked-lists `lists`, each linked-list is sorted in ascending order. Merge all the linked-lists into one sorted linked-list and return it.

**LeetCode**: https://leetcode.com/problems/merge-k-sorted-lists/
**Difficulty**: Hard

## Approach
Use a min heap to efficiently find the smallest element among all list heads.

## Solution
```python
import heapq

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
    
    def __lt__(self, other):
        return self.val < other.val

def mergeKLists(lists):
    heap = []
    for i, lst in enumerate(lists):
        if lst:
            heapq.heappush(heap, (lst.val, i, lst))
    
    dummy = ListNode(0)
    current = dummy
    
    while heap:
        val, idx, node = heapq.heappop(heap)
        current.next = node
        current = current.next
        if node.next:
            heapq.heappush(heap, (node.next.val, idx, node.next))
    
    return dummy.next
```

## Complexity
- **Time**: O(n log k)
- **Space**: O(k)
