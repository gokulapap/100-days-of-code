---
title: "Top K Frequent Elements"
description: "Placing N queens in NxN chess board without attacking other queen"
categories:
  - Hashmap
  - Heap
---

### Question

> Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

```
Example 1:

Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]

Example 2:

Input: nums = [1], k = 1
Output: [1]
```

### Code [CPP]

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        vector<int> ans;
        priority_queue<pair<int,int>> pq;
        map<int, int> counter;
        for(auto x: nums)
        {
            counter[x]++;
        }
        
        for(auto x: counter)
        {
            pq.push(make_pair(x.second, x.first));
        }
        
        while(k)
        {
            ans.push_back(pq.top().second);
            pq.pop();
            k--;
        }
        
        return ans;
    }
};
```


> Time Complexity = O(N)

> Space Complexity = O(N)
