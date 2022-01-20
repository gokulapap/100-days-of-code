---
title: "Koko Eating Bananas"
description: "the minimum integer k such that he can eat all the bananas within h hours"
categories:
  - binarysearch
  - array
---

### Question

> Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours. Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile. If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour. Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

> Return the minimum integer k such that she can eat all the bananas within h hou

```
Example 1:

Input: piles = [3,6,7,11], h = 8
Output: 4

Example 2:

Input: piles = [30,11,23,4,20], h = 5
Output: 30
```

### Code [C++]

```cpp
class Solution {
public:
    int minEatingSpeed(vector<int>& piles, int h) {
        int left = 1;
        int right = 10000000000;
        while(left < right)
        {
            int mid = (left+right)/2;
            int hrs = 0;
            for(auto x: piles)
            {
                if(x%mid == 0)
                    hrs += x/mid;
                else
                    hrs += (x/mid)+1;
            }
            if(hrs <= h)
                right = mid;
            else
                left = mid+1;
        }
        return right;
    }
};
```

> Time Complexity = O(logN)

> Space Complexity = O(1)
