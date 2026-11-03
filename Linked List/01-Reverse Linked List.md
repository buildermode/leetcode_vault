---
type: note
created_at: '2026-10-22T02:51:39.019Z'
updated_at: '2026-10-22T02:51:39.019Z'
---
## Problem
Given the head of a singly linked list, reverse the list and return the reversed list.

**LeetCode**: https://leetcode.com/problems/reverse-linked-list/
**Difficulty**: Easy

## Approach
Iteratively reverse the pointers by keeping track of the previous node.

## Solution
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverseList(head):
    prev = None
    current = head
    while current:
        next_temp = current.next
        current.next = prev
        prev = current
        current = next_temp
    return prev
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
