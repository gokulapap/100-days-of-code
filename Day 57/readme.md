---
title: "Maximum product of Two numbers"
description: "Return the maximum value of (nums[i]-1)*(nums[j]-1)"
categories:
  - Array
  - product
---

### Question

> Given the array of integers nums, you will choose two different indices i and j of that array. Return the maximum value of (nums[i]-1)*(nums[j]-1)

```
Example 1:

Input: nums = [3,4,5,2]
Output: 12 
Explanation: If you choose the indices i=1 and j=2 (indexed from 0), you will get the maximum value, that is, (nums[1]-1)*(nums[2]-1) = (4-1)*(5-1) = 3*4 = 12. 

Example 2:

Input: nums = [1,5,4,5]
Output: 16
Explanation: Choosing the indices i=1 and j=3 (indexed from 0), you will get the maximum value of (5-1)*(5-1) = 16.
```

### Code [C++]

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int maxproduct = 1;
        priority_queue<int> pq;
        for(auto x: nums)
            pq.push(x);
        
        maxproduct *= pq.top()-1;
        pq.pop();
        maxproduct *= pq.top()-1;
        
        return maxproduct;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
