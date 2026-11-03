---
type: note
created_at: '2026-10-22T02:51:41.703Z'
updated_at: '2026-10-22T02:51:41.703Z'
---
## Problem
Given the head of a linked list, determine if the linked list has a cycle in it. Return `true` if there is a cycle, otherwise `false`.

**LeetCode**: https://leetcode.com/problems/linked-list-cycle/
**Difficulty**: Easy

## Approach
Use Floyd's cycle detection algorithm (fast and slow pointers). If they meet, there's a cycle.

## Solution
```python
def hasCycle(head):
    if not head or not head.next:
        return False
    slow = head
    fast = head.next
    while slow != fast:
        if not fast or not fast.next:
            return False
        slow = slow.next
        fast = fast.next.next
    return True
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
