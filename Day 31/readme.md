---
title: "Richest Customer Wealth"
description: "Return the wealth that the richest customer has"
categories:
  - array
  - matrix
---

### Question

> You are given an m x n integer grid accounts where accounts[i][j] is the amount of money the i​​​​​​​​​​​th​​​​ customer has in the j​​​​​​​​​​​th​​​​ bank. Return the wealth that the richest customer has.

> A customer's wealth is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum wealth.

```
Input: accounts = [[1,2,3],[3,2,1]]
Output: 6
Explanation:
1st customer has wealth = 1 + 2 + 3 = 6
2nd customer has wealth = 3 + 2 + 1 = 6
Both customers are considered the richest with a wealth of 6 each, so return 6.
```

### Code [C++]

```cpp
class Solution {
public:
    int maximumWealth(vector<vector<int>>& accounts) {
        int max = 0;
        for(auto x: accounts)
        {
            int sum = accumulate(x.begin(), x.end(), 0);
            if(sum > max)
                max = sum;
        }
        
        return max;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
