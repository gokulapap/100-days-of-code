---
title: "Arithmetic Slices"
description: "return the number of arithmetic subarrays of nums
categories:
  - array
  - dp
---

### Question

> An integer array is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.

 - For example, [1,3,5,7,9], [7,7,7,7], and [3,-1,-5,-9] are arithmetic sequences.

> Given an integer array nums, return the number of arithmetic subarrays of nums.
> A subarray is a contiguous subsequence of the array.

```
Example 1:

Input: nums = [1,2,3,4]
Output: 3
Explanation: We have 3 arithmetic slices in nums: [1, 2, 3], [2, 3, 4] and [1,2,3,4] itself.

Example 2:

Input: nums = [1]
Output: 0
```

### Code [C++]

```cpp
class Solution {
public:
    int numberOfArithmeticSlices(vector<int>& A) {
        int n = A.size();
        if (n < 3) return 0;
        vector<int> dp(n, 0); 
        if (A[2]-A[1] == A[1]-A[0]) dp[2] = 1; 
        int result = dp[2];
        for (int i = 3; i < n; ++i) {

            if (A[i]-A[i-1] == A[i-1]-A[i-2]) 
                dp[i] = dp[i-1] + 1;
            result += dp[i]; 
        }
        return result;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
