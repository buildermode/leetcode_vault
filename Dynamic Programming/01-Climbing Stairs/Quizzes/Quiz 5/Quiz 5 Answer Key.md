---
type: note
created_at: '2026-10-30T23:25:40.862Z'
updated_at: '2026-10-30T23:25:40.862Z'
---
## Problem
You are climbing a staircase. It takes `n` steps to reach the top. Each time you can climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**LeetCode**: https://leetcode.com/problems/climbing-stairs/

---

### Question 13: Time Complexity - Reasoning & Value
**Why is the time complexity O(n) instead of O(2^n)? Explain the reasoning and the real-world value of this improvement.**

**Answer**:
**Reasoning**: DP computes each step `i` exactly once in a single loop from 1 to n. Each computation is O(1) (just one addition). Total operations = n iterations × 1 operation = O(n).

**Compared to naive recursion**: Without memoization, we recalculate overlapping subproblems exponentially. For `climbStairs(50)`, naive recursion would make over 2^50 (1 quadrillion) calls.

**Real-world value**: 
- O(n) solution: 50 operations → instant
- O(2^n) solution: 2^50 operations → would take years
- This is the difference between a feasible solution and an impossible one for large inputs.

---

### Question 14: Space Complexity - Reasoning & Value
**Why do we need O(n) space for the DP array? Can this be optimized, and if so, how?**

**Answer**:
**Why O(n)**: We store all values from step 1 to step n in the dp array. Each step's count is an integer that could theoretically be referenced later, so the straightforward approach allocates space for all of them.

**Can it be optimized?** Yes! Since `dp[i]` depends only on `dp[i-1]` and `dp[i-2]`, we don't need to store all previous values. We can use just two variables:

```python
def climbStairs(n):
    if n <= 2:
        return n
    prev2, prev1 = 1, 2  # dp[i-2] and dp[i-1]
    for i in range(3, n + 1):
        curr = prev1 + prev2  # dp[i]
        prev2, prev1 = prev1, curr  # shift forward
    return prev1
```

This reduces space to **O(1)**. Use this when space is critical (embedded systems, memory-constrained environments). For most cases, O(n) is acceptable and more readable.

---

### Question 15: Visual Understanding of Base Cases
**Describe the paths to reach step 2 in plain English. Why are there exactly 2 ways and not just 1?**

**Answer**: The two paths to reach step 2 are:
1. **Path 1**: Take 1 step, then take 1 step again → [1, 1]
2. **Path 2**: Take 2 steps at once → [2]

Why 2 ways, not 1? Because we can break the journey into steps in different ways. You could climb gradually (1+1) or skip ahead (2). Both are valid and distinct paths. This is why `dp[2] = 2`. This logic extends: at step 3, you could arrive from step 2 (via all the ways you reached step 2, then take 1 step) or from step 1 (via all the ways you reached step 1, then take 2 steps). This is why the recurrence works: each new step multiplies the possibilities by combining previous states.
