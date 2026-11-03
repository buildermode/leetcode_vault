---
type: note
created_at: '2026-10-22T02:51:51.674Z'
updated_at: '2026-10-22T02:51:51.674Z'
---
## Problem
You are given the head of a singly linked list. The list can be represented as: L₀ → L₁ → L₂ → ... → Lₙ₋₁ → Lₙ
Reorder the list to be: L₀ → Lₙ → L₁ → Lₙ₋₁ → L₂ → Lₙ₋₂ → ...

**LeetCode**: https://leetcode.com/problems/reorder-list/
**Difficulty**: Medium

## Approach
1. Find the middle of the list
2. Reverse the second half
3. Merge both halves

## Solution
```python
def reorderList(head):
    if not head or not head.next:
        return
    
    # Find middle
    slow, fast = head, head.next
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    
    # Reverse second half
    prev = None
    curr = slow.next
    slow.next = None
    while curr:
        next_temp = curr.next
        curr.next = prev
        prev = curr
        curr = next_temp
    
    # Merge
    l1, l2 = head, prev
    while l1 and l2:
        l1_next = l1.next
        l2_next = l2.next
        l1.next = l2
        l2.next = l1_next
        l1 = l1_next
        l2 = l2_next
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
