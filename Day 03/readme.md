---
title: "Last Stone Weight"
description: "Return the smallest possible weight of the left stone"
categories:
  - Coding
---

### Question

> You are given an array of integers stones where stones[i] is the weight of the ith stone.
> We are playing a game with the stones. On each turn, we choose the heaviest two stones and smash them together. Suppose the heaviest two stones have weights x and y with x <= y. The result of this smash is:
>    If x == y, both stones are destroyed, and
>    If x != y, the stone of weight x is destroyed, and the stone of weight y has new weight y - x.
> At the end of the game, there is at most one stone left.

> Return the smallest possible weight of the left stone. If there are no stones left, return 0.

### Code [CPP]

```cpp
class Solution {
public:
    int lastStoneWeight(vector<int>& stones) {
        priority_queue<int> pq(stones.begin(), stones.end());
        int a,b;
        while(true)
        {
            if(pq.size() == 0) return 0;
            if(pq.size() == 1) return pq.top();
            a = pq.top();
            pq.pop();
            b = pq.top();
            pq.pop();
            if(a == b)
                continue;
            else
                pq.push(a-b);
        }
    }
};
```


> Time Complexity = O(N)

> Space Complexity = O(1)
