---
type: note
created_at: '2026-10-30T23:25:20.491Z'
updated_at: '2026-10-30T23:25:20.491Z'
---
## Problem
You are climbing a staircase. It takes `n` steps to reach the top. Each time you can climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**LeetCode**: https://leetcode.com/problems/climbing-stairs/

---

### Question 7: Implementation Challenge
**Write the complete DP solution for climbing stairs.**

**Answer**:
```python
def climbStairs(n):
    if n <= 2:
        return n
    dp = [0] * (n + 1)
    dp[1], dp[2] = 1, 2
    for i in range(3, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    return dp[n]
```

**Expected outputs**:
- `climbStairs(1)` → 1
- `climbStairs(2)` → 2
- `climbStairs(3)` → 3
- `climbStairs(4)` → 5
- `climbStairs(5)` → 8

---

### Question 8: Key Insight Application
**Why is this a "classic DP pattern"? What properties make it suitable for dynamic programming?**

**Answer**: 
- **Overlapping subproblems**: To solve `dp[5]`, we need `dp[4]` and `dp[3]`. To solve `dp[4]`, we also need `dp[3]`. This recalculation is avoided by storing results.
- **Optimal substructure**: The best way to reach step `n` depends only on the solutions to reaching steps `n-1` and `n-2`.
- **Exponential growth without DP**: Without memoization, recursive calls would explore the same subproblems exponentially, making naive recursion inefficient.

---

### Question 9: Time & Space Complexity
**What are the time and space complexities of the DP solution, and could we do better?**

**Answer**:
- **Time**: O(n) - we compute each step once
- **Space**: O(n) - we store all values in the dp array

**Space optimization**: Yes! Since `dp[i]` only depends on `dp[i-1]` and `dp[i-2]`, we could use just two variables instead of an array:
```python
def climbStairs(n):
    if n <= 2:
        return n
    prev, curr = 1, 2
    for i in range(3, n + 1):
        prev, curr = curr, prev + curr
    return curr
```
This reduces space to O(1).
