---
type: note
created_at: '2026-10-22T02:53:52.361Z'
updated_at: '2026-10-22T02:53:52.361Z'
---
## Problem
Given a string `s` and a dictionary of strings `wordDict`, return `true` if `s` can be segmented into a space-separated sequence of dictionary words.

**LeetCode**: https://leetcode.com/problems/word-break/
**Difficulty**: Medium

## Approach
DP approach. dp[i] is true if substring s[0:i] can be segmented.

## Solution
```python
def wordBreak(s, wordDict):
    word_set = set(wordDict)
    dp = [False] * (len(s) + 1)
    dp[0] = True
    for i in range(1, len(s) + 1):
        for j in range(i):
            if dp[j] and s[j:i] in word_set:
                dp[i] = True
                break
    return dp[len(s)]
```

## Complexity
- **Time**: O(n²)
- **Space**: O(n)
