---
type: note
created_at: '2026-10-30T19:06:04.445Z'
updated_at: '2026-10-30T19:06:04.445Z'
---
## Sample Quiz: Climbing Stairs
### Question 1: Conceptual Understanding (Who, What, Where, When, Why)

**In your own words, what is the climbing stairs problem asking you to calculate?**
**Answer**: The climbing stairs problem asks you to count all the distinct (different) ways to reach the top of a staircase with `n` steps, where at each move you can climb either 1 step or 2 steps. The goal is to find the total number of unique combinations of 1-step and 2-step moves that get you from the bottom to the top.

---

### Question 2: Real-World Application
**In the feature recommendation system example from the encoding, what do the "auto-skip actions" represent in the staircase context?**

**Answer**: Auto-skip actions represent taking 2 steps at once. A user can either click through one page (1 step) or auto-skip to the next page (2 steps), creating multiple unique navigation paths through the wizard.

---

### Question 3: Base Cases
**What are the base cases for the Climbing Stairs DP solution, and why?**

**Answer**: 
- `dp[1] = 1` (only one way to reach step 1: take 1 step)
- `dp[2] = 2` (two ways to reach step 2: take 1+1 steps or take 2 steps)

These are the foundation because every other step builds upon these two scenarios.

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
