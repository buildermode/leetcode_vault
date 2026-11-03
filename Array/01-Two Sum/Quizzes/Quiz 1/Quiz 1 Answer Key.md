---
type: note
created_at: '2026-10-31T19:02:45.664Z'
updated_at: '2026-10-31T19:02:45.664Z'
---

## Problem
Given an array of integers `nums` and an integer `target`, return the indices of the two numbers that add up to `target`. Each input has exactly one solution, and the same element cannot be used twice.

**Example:**
- Input: `nums = [2, 7, 11, 15]`, `target = 9`
- Output: `[0, 1]` (because `nums[0] + nums[1] = 2 + 7 = 9`)

---

### Question 1
**Explain what makes the Two Sum problem distinct from simply finding any two numbers that add to a target. Why does the problem specifically ask for indices rather than the values themselves?**

**Answer:** The Two Sum problem differs from value-finding in a critical way: **returning indices preserves the location information of the solution, not just the numbers themselves**. This is essential because:

1. **Traceability**: Indices allow you to trace back to the original elements, enabling verification, logging, and auditing. In the context of real-world applications (transactions, users, timestamps), knowing *which* elements form the pair matters more than just knowing the sum exists.

2. **Ambiguity resolution**: Multiple pairs of values might sum to the target, but only specific positions in the array are the "answer." For example, in `[5, 4, 5]` with target 9, both positions (0,1) and (0,2) sum to 9. The problem asks for indices to disambiguate.

3. **Algorithm constraint**: The "same element cannot be used twice" rule refers to *indices*, not values. This constraint only makes sense when thinking in terms of positions. Returning indices directly proves we understand and respect this constraint.

4. **Practical utility**: In real applications (fraud detection, transaction matching, user profiling), you need the *positions* in your data to take action—flag that specific transaction, investigate those users, update those records.

---

### Question 2
**Consider you're building a payment fraud detection system that receives a stream of transactions. Your task is to identify pairs of transactions from the same user that together exceed a suspicious threshold (e.g., two transactions totaling $10,000 in an hour). How would the Two Sum problem's approach apply to this scenario? What would the "array" be, what would the "target" be, and why would returning the indices be more useful than returning the values?**

**Answer:** In this fraud detection scenario, the Two Sum approach maps directly:

- **Array**: The list of transaction amounts for a given user (e.g., `[500, 9200, 300, 800]`)
- **Target**: The suspicious threshold (e.g., `10000`)
- **Goal**: Find indices of two transactions that together exceed the threshold

Why indices matter more than values:
1. **Action items**: Once you find that transactions at indices [1, 3] (values 9200 and 800) sum to 10000, you can immediately flag transaction IDs `txn_1` and `txn_3`, block them, and alert compliance.

2. **Timestamp preservation**: Transaction indices correlate with timestamps. Finding indices [1, 3] tells you these two specific transactions (with their unique timestamps and metadata) are the suspicious pair, not just "two amounts that add up."

3. **Proof of violation**: In fraud proceedings, you need to show *exactly which transactions* triggered the alert. Saying "the user had two transactions totaling $10k" is vague; saying "transaction #9485 and transaction #9487 from user X created this violation" is actionable evidence.

4. **Prevention of duplicates**: If you report values instead of indices, you might flag the same logical pair multiple times if amounts repeat. Indices ensure one-time reporting.

---

### Question 3
**Define what "complement" means in the context of Two Sum, and explain why this reframing helps us solve the problem more efficiently than checking all pairs.**

**Answer:** 

**Complement definition**: For a given number `num` and target `target`, the complement is `complement = target - num`. It's the value that, when added to `num`, yields the target.

Example: In `[2, 7, 11, 15]` with target 9:
- When we see `2`, its complement is `9 - 2 = 7` (and 7 exists in the array)
- When we see `7`, its complement is `9 - 7 = 2` (and 2 already exists in our map)

**Why this reframing is more efficient**:

1. **Transforms the problem**: Instead of asking "do any two numbers pair up?" (O(n²) complexity), we ask "for each number, is its complement already stored?" (O(n) with a hash map).

2. **One-pass solution**: With the brute force approach, you'd need nested loops:
   ```
   for each element at position i:
       for each element at position j > i:
           if nums[i] + nums[j] == target: return [i, j]  // O(n²)
   ```
   
   With the complement approach:
   ```
   for each element at position i:
       if complement exists in map: return [map[complement], i]  // O(n)
       store the element in map
   ```

3. **Hash map lookup is instant**: Building a map as you iterate costs O(1) per insertion. Checking if a complement exists is O(1) lookup. Total: O(n).

4. **Concrete comparison** (for n=1,000,000):
   - Brute force: 1 trillion operations (unacceptable for real-time fraud detection)
   - Hash map: 1 million operations (milliseconds, perfect for fraud systems)

This reframing is the "aha moment" of the Two Sum problem and appears in many advanced algorithms. It's why understanding this problem deeply helps you recognize similar patterns in larger problems.

---
