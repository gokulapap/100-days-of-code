---
title: "Combination Sum"
description: " return a list of all unique combinations of nums sums target"
categories:
  - array
  - backtracking
---

### Question

> Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.
> The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

> It is guaranteed that the number of unique combinations that sum up to target is less than 150 combinations for the given input.

```
Example 1:

Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]

Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
```

### Code [C++]

```cpp
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& nums, int target) {
        vector<vector<vector <int>>> dp(target+1);
        dp[0]={{}};
        for(int &i:nums)
        {
            for(int j=i;j<=target;j++)
            {
                for(auto v:dp[j-i])
                {
                    v.push_back(i);
                    dp[j].push_back(v);
                }
            }
        }
        return dp[target];
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
