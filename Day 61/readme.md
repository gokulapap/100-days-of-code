---
title: "Delete and Earn"
description: "Return the maximum number of points you can earn"
categories:
  - array
  - dynamic programming
---

### Question

> You are given an integer array nums. You want to maximize the number of points you get by performing the following operation any number of times:
> Pick any nums[i] and delete it to earn nums[i] points. Afterwards, you must delete every element equal to nums[i] - 1 and every element equal to nums[i] + 1.

> Return the maximum number of points you can earn by applying the above operation some number of times.

```
Example 1:

Input: nums = [3,4,2]
Output: 6
Explanation: You can perform the following operations:
- Delete 4 to earn 4 points. Consequently, 3 is also deleted. nums = [2].
- Delete 2 to earn 2 points. nums = [].
You earn a total of 6 points.

Example 2:

Input: nums = [2,2,3,3,3,4]
Output: 9
Explanation: You can perform the following operations:
- Delete a 3 to earn 3 points. All 2's and 4's are also deleted. nums = [3,3].
- Delete a 3 again to earn 3 points. nums = [3].
- Delete a 3 once more to earn 3 points. nums = [].
You earn a total of 9 points.
```

### Code [C++]

```cpp
class Solution {
public:
    int deleteAndEarn(vector<int>& nums) {
        int n = 10001;
        
        vector<int> sum(n, 0);
        vector<int> dp(n, 0);
    
        for(auto num: nums) {
            sum[num] += num;
        }
   
        dp[0] = 0;
        dp[1] = sum[1];
        
        for(int i=2; i<n; i++) {
            dp[i] = max(dp[i-2] + sum[i], dp[i-1]);
        }
    
        return dp[n-1];
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
