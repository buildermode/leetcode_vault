---
type: note
created_at: '2026-10-22T02:53:29.552Z'
updated_at: '2026-10-22T02:53:29.552Z'
---
## Problem
There are n gas stations along a circular route where the amount of gas at each station is `gas[i]` and the cost of traveling to the next station is `cost[i]`. You start with an empty tank and can only travel to the next station if the gas in your tank is greater than or equal to the cost. Given two integer arrays `gas` and `cost`, return the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return -1.

**LeetCode**: https://leetcode.com/problems/gas-station/
**Difficulty**: Medium

## Approach
Greedy approach with validation. If total gas is insufficient, return -1. Otherwise, find the starting point.

## Solution
```python
def canCompleteCircuit(gas, cost):
    total_gas = 0
    current_gas = 0
    start = 0
    for i in range(len(gas)):
        total_gas += gas[i] - cost[i]
        current_gas += gas[i] - cost[i]
        if current_gas < 0:
            start = i + 1
            current_gas = 0
    return start if total_gas >= 0 else -1
```

## Complexity
- **Time**: O(n)
- **Space**: O(1)
