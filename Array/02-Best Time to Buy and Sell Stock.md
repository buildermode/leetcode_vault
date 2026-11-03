---
type: note
created_at: '2026-10-22T02:50:55.198Z'
updated_at: '2026-10-22T02:50:55.198Z'
---
## Problem
You are given an array `prices` where `prices[i]` is the price of a given stock on the ith day. Find the maximum profit you can achieve. You may complete at most one transaction (buy and sell).

**LeetCode**: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
**Difficulty**: Easy

## Approach
Track the minimum price seen so far and calculate profit at each step. Keep the maximum profit.

## Solution
```python
def maxProfit(prices):
    min_price = float('inf')
    max_profit = 0
    for price in prices:
        min_price = min(min_price, price)
        profit = price - min_price
        max_profit = max(max_profit, profit)
    return max_profit
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
