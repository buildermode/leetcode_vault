---
type: note
created_at: '2026-10-22T02:54:20.586Z'
updated_at: '2026-10-22T02:54:20.586Z'
---
## Problem
Write a function that takes the binary representation of a positive integer and returns the number of set bits it has (also known as the Hamming weight).

**LeetCode**: https://leetcode.com/problems/number-of-1-bits/
**Difficulty**: Easy

## Approach
Count the number of 1 bits by checking each bit or using Brian Kernighan's algorithm.

## Solution
```python
def hammingWeight(n):
    count = 0
    while n:
        count += n & 1
        n >>= 1
    return count

# Or using Brian Kernighan's algorithm
def hammingWeight(n):
    count = 0
    while n:
        n &= n - 1  # Removes the rightmost 1 bit
        count += 1
    return count
```

## Complexity
- **Time**: O(log n)
- **Space**: O(1)
