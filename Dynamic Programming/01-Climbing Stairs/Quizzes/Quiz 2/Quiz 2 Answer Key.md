---
type: note
created_at: '2026-10-30T23:25:12.412Z'
updated_at: '2026-10-30T23:25:12.412Z'
---
## Problem
You are climbing a staircase. It takes `n` steps to reach the top. Each time you can climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**LeetCode**: https://leetcode.com/problems/climbing-stairs/

---

### Question 4: Recurrence Relation
**Explain the recurrence relation `dp[i] = dp[i-1] + dp[i-2]` in plain English.**

**Answer**: To reach step `i`, you can only arrive from two places: step `i-1` (by taking 1 step) or step `i-2` (by taking 2 steps). Therefore, the total number of distinct ways to reach step `i` is the sum of ways to reach both predecessors.

---

### Question 5: Step-by-Step Execution
**Calculate the number of distinct ways to reach step 4. Show your work.**

**Answer**:
- `dp[1] = 1`
- `dp[2] = 2`
- `dp[3] = dp[2] + dp[1] = 2 + 1 = 3`
- `dp[4] = dp[3] + dp[2] = 3 + 2 = 5`

There are 5 distinct ways to reach step 4:
1. 1+1+1+1
2. 1+1+2
3. 1+2+1
4. 2+1+1
5. 2+2

---

### Question 6: Pattern Recognition
**What famous mathematical sequence appears in the Climbing Stairs problem, and why?**

**Answer**: The Fibonacci sequence. Each step's count is the sum of the two previous counts (1, 2, 3, 5, 8, 13...). This happens because the recurrence relation `dp[i] = dp[i-1] + dp[i-2]` is the defining characteristic of Fibonacci numbers.
