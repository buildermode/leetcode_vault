---
type: note
created_at: '2026-10-22T02:51:47.932Z'
updated_at: '2026-10-22T02:51:47.932Z'
---
## Problem
Given the head of a linked list, remove the nth node from the end of the list and return the head of the list.

**LeetCode**: https://leetcode.com/problems/remove-nth-node-from-end-of-list/
**Difficulty**: Medium

## Approach
Use two pointers with a gap of n. Move both until the fast pointer reaches the end.

## Solution
```python
def removeNthFromEnd(head, n):
    dummy = ListNode(0)
    dummy.next = head
    fast = dummy
    slow = dummy
    for _ in range(n + 1):
        if not fast:
            return head
        fast = fast.next
    while fast:
        fast = fast.next
        slow = slow.next
    slow.next = slow.next.next
    return dummy.next
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
