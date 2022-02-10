---
title: "Subarray Sum Equals K"
description: "return total number of continuous subarrays whose sum equals to k"
categories:
  - sum
  - subarray
---

### Question

> Given an array of integers nums and an integer k, return the total number of continuous subarrays whose sum equals to k.
 
```
Example 1:

Input: nums = [1,1,1], k = 2
Output: 2

Example 2:

Input: nums = [1,2,3], k = 3
Output: 2
```

### Code [C++]

```cpp
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        unordered_map<int, int> seen = {make_pair(0,1)};
        int count = 0, sum = 0;
        for (auto n: nums) {
            sum += n;
            count += seen[sum - k];
            seen[sum]++;
        }
        return count;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
