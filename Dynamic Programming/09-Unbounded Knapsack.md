---
type: note
created_at: '2026-10-22T02:53:58.234Z'
updated_at: '2026-10-22T02:53:58.234Z'
---
## Problem
You are given weights and values of items, you need to put these items in a knapsack of capacity W to get the maximum total value. You can take an unlimited quantity of each item.

**LeetCode**: Similar to coin change variations
**Difficulty**: Medium

## Approach
DP approach similar to coin change. Build up solutions for increasing capacities.

## Solution
```python
def unboundedKnapsack(weights, values, W):
    dp = [0] * (W + 1)
    for i in range(1, W + 1):
        for j in range(len(weights)):
            if weights[j] <= i:
                dp[i] = max(dp[i], dp[i - weights[j]] + values[j])
    return dp[W]
```

## Complexity
- **Time**: O(W * n)
- **Space**: O(W)
