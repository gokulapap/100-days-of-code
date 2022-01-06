---
title: "Kadane's Algorithm"
description: "Maximum subarray Sum"
categories:
  - Coding
---

### Question

> Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum. A subarray is a contiguous part of an array.

```
Input: arr = [1,4,5,6,-2,-7,-2,-1]
Output: 16
```

### Code [C++]

```cpp

class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int maxsum = INT_MIN, cursum = 0;
        for(int i=0; i<nums.size(); i++)
        {
            cursum = max(nums[i], cursum+=nums[i]);
            maxsum = max(maxsum, cursum);
        }      
        return maxsum;
    }
};

```

> Time Complexity = O(N)

> Space Complexity = O(1)
