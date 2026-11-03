---
type: note
created_at: '2026-10-30T23:25:29.157Z'
updated_at: '2026-10-30T23:25:29.157Z'
---
## Problem
You are climbing a staircase. It takes `n` steps to reach the top. Each time you can climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**LeetCode**: https://leetcode.com/problems/climbing-stairs/

---

### Question 10: Extension Challenge
**What if you could take 1, 2, or 3 steps at a time? How would the recurrence relation change?**

**Answer**: The recurrence relation would become:
`dp[i] = dp[i-1] + dp[i-2] + dp[i-3]`

Because now you can reach step `i` from any of the three previous positions (step `i-1`, `i-2`, or `i-3`). The base cases would be:
- `dp[1] = 1`
- `dp[2] = 2` (1+1 or 2)
- `dp[3] = 4` (1+1+1, 1+2, 2+1, or 3)

---

### Question 11: Overlapping Subproblems
**Explain what "overlapping subproblems" means in the climbing stairs problem. Why does naive recursion fail because of this?**

**Answer**: Overlapping subproblems means the same subproblem gets computed multiple times. In naive recursion:
```
climbStairs(5) calls climbStairs(4) and climbStairs(3)
climbStairs(4) calls climbStairs(3) and climbStairs(2)
climbStairs(3) calls climbStairs(2) and climbStairs(1)  [called again!]
```
Notice that `climbStairs(3)` is computed twice, `climbStairs(2)` three times, etc. This exponential duplication makes the time complexity O(2^n). DP solves this by computing each value once and storing it.

---

### Question 12: Why Dynamic Programming?
**Why is dynamic programming the right choice for this problem? List the two critical DP properties that apply here.**

**Answer**: The two properties are:
1. **Overlapping Subproblems**: Computing `ways(n)` requires computing `ways(n-1)` and `ways(n-2)` repeatedly in naive recursion.
2. **Optimal Substructure**: The solution to `ways(n)` is built entirely from solutions to `ways(n-1)` and `ways(n-2)` via a simple addition. There's no better way to solve step `n` than to combine the solutions of its predecessors.

These two properties together make DP ideal. Alternative approaches (greedy, backtracking) would either fail to find all paths or be inefficient.
