---
type: note
created_at: '2026-10-30T23:25:01.988Z'
updated_at: '2026-10-30T23:25:01.988Z'
---
## Problem
You are climbing a staircase. It takes `n` steps to reach the top. Each time you can climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**LeetCode**: https://leetcode.com/problems/climbing-stairs/

---

### Question 1: Conceptual Understanding
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
