---
type: note
created_at: '2026-10-22T02:53:37.242Z'
updated_at: '2026-10-22T02:53:37.242Z'
---
## Problem
You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money. Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

**LeetCode**: https://leetcode.com/problems/coin-change/
**Difficulty**: Medium

## Approach
DP approach. dp[i] represents the minimum coins needed to make amount i.

## Solution
```python
def coinChange(coins, amount):
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    for i in range(1, amount + 1):
        for coin in coins:
            if coin <= i:
                dp[i] = min(dp[i], dp[i - coin] + 1)
    return dp[amount] if dp[amount] != float('inf') else -1
```

## Complexity
- **Time**: O(amount * n)
- **Space**: O(amount)
