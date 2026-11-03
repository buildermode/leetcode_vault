---
type: note
created_at: '2026-10-22T02:53:01.791Z'
updated_at: '2026-10-22T02:53:01.791Z'
---
## Problem
Given two words, `beginWord` and `endWord`, and a dictionary `wordList`, return the number of words in the shortest transformation sequence from `beginWord` to `endWord`, or 0 if no such sequence exists. You must change exactly one letter in each step, and each transformed word must exist in the word list.

**LeetCode**: https://leetcode.com/problems/word-ladder/
**Difficulty**: Hard

## Approach
BFS to find the shortest path. Build a graph where edges connect words that differ by one letter.

## Solution
```python
def ladderLength(beginWord, endWord, wordList):
    from collections import deque
    word_set = set(wordList)
    if endWord not in word_set:
        return 0
    
    queue = deque([(beginWord, 1)])
    visited = {beginWord}
    
    while queue:
        word, length = queue.popleft()
        if word == endWord:
            return length
        
        for i in range(len(word)):
            for c in 'abcdefghijklmnopqrstuvwxyz':
                next_word = word[:i] + c + word[i+1:]
                if next_word in word_set and next_word not in visited:
                    visited.add(next_word)
                    queue.append((next_word, length + 1))
    return 0
```

## Complexity
- **Time**: O(n * l * 26)
- **Space**: O(n)
