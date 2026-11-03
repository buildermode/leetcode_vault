---
type: note
created_at: '2026-10-22T02:51:45.065Z'
updated_at: '2026-10-22T02:51:45.065Z'
---
## Problem
You are given the heads of two sorted linked lists `list1` and `list2`. Merge the two lists in a single sorted list. The list should be made by splicing together the nodes of the two lists.

**LeetCode**: https://leetcode.com/problems/merge-two-sorted-lists/
**Difficulty**: Easy

## Approach
Compare nodes from both lists and append the smaller one to the result.

## Solution
```python
def mergeTwoLists(list1, list2):
    dummy = ListNode(0)
    current = dummy
    while list1 and list2:
        if list1.val <= list2.val:
            current.next = list1
            list1 = list1.next
        else:
            current.next = list2
            list2 = list2.next
        current = current.next
    current.next = list1 if list1 else list2
    return dummy.next
```

## Complexity
- **Time**: O(n + m)
- **Space**: O(1)
