---
type: note
created_at: '2026-10-22T02:51:19.195Z'
updated_at: '2026-10-22T02:51:19.195Z'
---
## Problem
Given a string `s` containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid. A valid string requires proper closing of brackets in the correct order.

**LeetCode**: https://leetcode.com/problems/valid-parentheses/
**Difficulty**: Easy

## Approach
Use a stack. Push opening brackets, and pop when closing brackets match. String is valid if stack is empty at the end.

## Solution
```python
def isValid(s):
    stack = []
    pairs = {'(': ')', '{': '}', '[': ']'}
    for char in s:
        if char in pairs:
            stack.append(char)
        else:
            if not stack or pairs[stack.pop()] != char:
                return False
    return len(stack) == 0
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
