---
type: note
created_at: '2026-10-31T19:02:32.025Z'
updated_at: '2026-10-31T19:02:32.025Z'
---

## Problem
Given an array of integers `nums` and an integer `target`, return the indices of the two numbers that add up to `target`. Each input has exactly one solution, and the same element cannot be used twice.

**Example:**
- Input: `nums = [2, 7, 11, 15]`, `target = 9`
- Output: `[0, 1]` (because `nums[0] + nums[1] = 2 + 7 = 9`)

---

## Q1: Conceptual Understanding
Explain what makes the Two Sum problem distinct from simply finding any two numbers that add to a target. Why does the problem specifically ask for **indices** rather than the values themselves?




---

## Q2: Real-World Application
Consider you're building a payment fraud detection system that receives a stream of transactions. Your task is to identify pairs of transactions from the same user that together exceed a suspicious threshold (e.g., two transactions totaling $10,000 in an hour). 

How would the Two Sum problem's approach apply to this scenario? What would the "array" be, what would the "target" be, and why would returning the indices be more useful than returning the values?




---

## Q3: The Complement Pattern
A key insight of the solution is recognizing that instead of checking "what pairs sum to the target?", we can ask "for each number, does its complement exist?" 

Define what "complement" means in the context of Two Sum, and explain why this reframing helps us solve the problem more efficiently than checking all pairs.
