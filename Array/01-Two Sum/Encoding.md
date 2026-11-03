---
type: note
created_at: '2026-10-31T19:01:40.065Z'
updated_at: '2026-10-31T19:01:40.065Z'
---

## 1. Who, What, Where, When, Why, How
**Who**: Array problems that require finding pairs of elements.

**What**: Given an array of integers and a target sum, find the indices of the two distinct numbers that add up to the target.

**Where**: This appears in LeetCode, interviews, and real-world scenarios like balance calculations or complementary pair detection.

**When**: Use this approach whenever you need to find a pair of elements meeting a sum condition, or more generally, when looking for complements of values.

**Why**: Finding pairs efficiently is foundational for solving more complex problems involving multiple constraints, ranges, or nested searches.

**How**: Store seen numbers in a hash map as you iterate, checking if each number's complement already exists in the map.

## 2. Real-World Example
**Payment Reconciliation**: Imagine you're processing refunds for a SaaS platform. You have a list of transactions and need to match refund requests with original payments. For each refund amount, you need to find if there's a corresponding pair of transactions that together equal a target settlement amount. The hash map approach lets you do this in one pass through the data, critical for processing thousands of transactions efficiently.

Another example: **Fraud Detection** - finding pairs of suspicious transactions that together exceed a fraud threshold, where you need to return the transaction IDs for investigation.

## 3. Step-by-Step Explanation
1. **Initialize a hash map** to store numbers we've already seen, mapped to their indices.

2. **Iterate through the array** with an index:
   - For each number `num`, calculate its complement: `complement = target - num`
   - Check if this complement exists in our map
   
3. **If the complement exists**:
   - We found our pair! Return the index of the complement (from the map) and the current index

4. **If the complement doesn't exist yet**:
   - Store the current number and its index in the map
   - Continue to the next element

5. **Why we check before storing**: We want to avoid using the same element twice. By checking if the complement exists before adding the current number, we ensure the complement came from an earlier position.

## 4. Visual Description
**Example**: `nums = [2, 7, 11, 15]`, `target = 9`

```
Index:    0  1  2   3
Value:    2  7  11  15
Target:   9

Step 1: i=0, num=2
  complement = 9-2 = 7
  map = {}
  7 not in map → store map[2] = 0
  
Step 2: i=1, num=7
  complement = 9-7 = 2
  map = {2: 0}
  2 IS in map! → return [map[2], 1] = [0, 1] ✓
```

**Another example with no early solution**: `nums = [3, 2, 4]`, `target = 6`

```
Index:    0  1  2
Value:    3  2  4
Target:   6

Step 1: i=0, num=3
  complement = 6-3 = 3
  map = {}
  3 not in map → store map[3] = 0
  
Step 2: i=1, num=2
  complement = 6-2 = 4
  map = {3: 0}
  4 not in map → store map[2] = 1
  
Step 3: i=2, num=4
  complement = 6-4 = 2
  map = {3: 0, 2: 1}
  2 IS in map! → return [map[2], 2] = [1, 2] ✓
```

**Pattern**: As you build the map, you're creating a "complement lookup table" that grows as you move through the array. The moment you encounter a number whose complement exists in that table, you have your answer.

## 5. Key Insight to Remember
**The Complement Lookup Pattern**: Instead of checking every pair (O(n²)), transform the problem into "does the complement already exist?" This shifts the bottleneck from comparison to lookup. Hash maps make complements retrieval O(1), so the entire problem becomes O(n).

The elegant insight is the **inversion of perspective**: rather than asking "what pairs sum to target?", ask "for each number, is its complement available?" This is a subtle but powerful reframing that appears in many two-pointer and hash map problems.

## 6. Why This Approach?
**Why the hash map approach is optimal**:

- **Optimal Substructure**: If `nums[i] + nums[j] = target`, then the problem reduces to "find j such that `nums[j] = target - nums[i]`". This subproblem is independent once we fix `i`.
- **Hash Map Property**: Hash maps provide O(1) average lookup, allowing us to check if a complement exists instantly.

**Why alternatives fail or are suboptimal**:

- **Brute Force (nested loops)**: O(n²) time - for n=100,000, this is 10 billion operations.
- **Sorting + Two Pointers**: O(n log n) - faster than brute force, but slower than O(n) and loses original indices (requires additional tracking).
- **Nested hash map checks**: Some approaches use two passes or check `complement in map` multiple times inefficiently.

**Why this approach works in one pass**:
- We don't need to search the entire remaining array for each element
- We don't need to sort and use two pointers
- Each element is processed exactly once, building the solution incrementally

## 7. Time Complexity: Reasoning & Value
**Why O(n)?**
- Single loop through the array: `n` iterations
- Inside the loop, only O(1) operations:
  - Hash map lookup: `complement in map` → O(1) average case
  - Hash map insertion: `map[num] = i` → O(1) average case
- Total: n × O(1) = **O(n)**

**Value comparison** (for n=1,000,000):
- **Brute Force O(n²)**: 1 trillion operations (unacceptable)
- **Sorting O(n log n)**: ~20 million operations (reasonable)
- **Hash Map O(n)**: 1 million operations (optimal) ✓

For finding pairs in massive transaction logs (millions of records), O(n) vs O(n²) is the difference between milliseconds and hours.

**Impact**: This is why hash map solutions dominate interview questions—they demonstrate understanding of how data structures unlock optimal complexity.

## 8. Space Complexity: Reasoning & Value
**Why O(n)?**
- We store up to `n-1` numbers in the hash map (worst case: no pair found until the end)
- Each entry takes O(1) space (int index, int value)
- Total: **O(n)** space

**Optimization possibilities**:

1. **Two-Pass Sort + Two Pointers**: O(1) extra space
   - Sort array, track original indices separately
   - Use two pointers from ends
   - Trade-off: O(n log n) time instead of O(n)
   - Use when: Space is extremely constrained

2. **In-Place Modifications** (NOT recommended here):
   - Modifying input array is generally a bad practice
   - Loses original indices, complicating the solution

**Trade-offs table**:

| Approach | Time | Space | Notes |
|----------|------|-------|-------|
| Hash Map | O(n) | O(n) | Best for most cases ✓ |
| Sort + Two Pointers | O(n log n) | O(1) | Use if space is critical |
| Brute Force | O(n²) | O(1) | Only for tiny inputs |

**When to use each**:
- **Hash Map O(n) space**: Standard choice—clear intent, optimal complexity
- **Two Pointers O(1) space**: In embedded systems or when processing huge lists with tight memory constraints
- **Brute Force**: Never in production (but good for teaching correctness)

The O(n) space is a fair trade-off for O(n) time; you're not overcomplicating a simple case with unnecessary optimization.
