---
type: note
created_at: '2026-10-22T02:55:03.062Z'
updated_at: '2026-10-22T02:55:03.062Z'
---
## Problem
Design a simplified version of Twitter. Implement the Twitter class with postTweet, getNewsFeed, follow, and unfollow methods.

**LeetCode**: https://leetcode.com/problems/design-twitter/
**Difficulty**: Medium

## Approach
Use a timestamp, user followers map, and a max heap to retrieve the most recent tweets.

## Solution
```python
from collections import defaultdict
import heapq

class Twitter:
    def __init__(self):
        self.user_tweets = defaultdict(list)
        self.user_follows = defaultdict(set)
        self.timestamp = 0
    
    def postTweet(self, userId, tweetId):
        self.timestamp += 1
        self.user_tweets[userId].append((self.timestamp, tweetId))
    
    def getNewsFeed(self, userId):
        heap = []
        for followee_id in self.user_follows[userId] | {userId}:
            if followee_id in self.user_tweets:
                idx = len(self.user_tweets[followee_id]) - 1
                ts, tweet = self.user_tweets[followee_id][idx]
                heapq.heappush(heap, (-ts, followee_id, idx, tweet))
        
        result = []
        while heap and len(result) < 10:
            neg_ts, followee_id, idx, tweet = heapq.heappop(heap)
            result.append(tweet)
            if idx > 0:
                idx -= 1
                ts, tweet = self.user_tweets[followee_id][idx]
                heapq.heappush(heap, (-ts, followee_id, idx, tweet))
        
        return result
    
    def follow(self, followerId, followeeId):
        self.user_follows[followerId].add(followeeId)
    
    def unfollow(self, followerId, followeeId):
        self.user_follows[followerId].discard(followeeId)
```

## Complexity
- **PostTweet**: O(1)
- **GetNewsFeed**: O(k log k)
- **Follow/Unfollow**: O(1)
