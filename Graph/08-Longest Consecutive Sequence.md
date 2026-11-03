---
type: note
created_at: '2026-10-22T02:52:48.880Z'
updated_at: '2026-10-22T02:52:48.880Z'
---
## Problem
Given an unsorted array of integers `nums`, return the length of the longest consecutive elements sequence. You must write an algorithm that runs in O(n) time.

**LeetCode**: https://leetcode.com/problems/longest-consecutive-sequence/
**Difficulty**: Medium

## Approach
Use a set to store all numbers. For each number, check if it's the start of a sequence and count the length.

## Solution
```python
def longestConsecutive(nums):
    if not nums:
        return 0
    num_set = set(nums)
    longest = 0
    for num in num_set:
        if num - 1 not in num_set:  # Start of a sequence
            current = num
            count = 1
            while current + 1 in num_set:
                current += 1
                count += 1
            longest = max(longest, count)
    return longest
```

## Complexity
- **Time**: O(n)
- **Space**: O(n)
