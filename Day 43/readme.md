---
title: "Single number"
description: "every element appears twice except for one. find that single one"
categories:
  - array
  - bit manipulation
---

### Question

> Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.
> You must implement a solution with a linear runtime complexity and use only constant extra space.

```
Example 1:

Input: nums = [2,2,1]
Output: 1

Example 2:

Input: nums = [4,1,2,1,2]
Output: 4
```

### Code [C++]

```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        map<int, int> counter;
        for(int x: nums)
        {
            counter[x] += 1;
        }
        
        for(auto x: counter)
        {
            if(x.second == 1)
                return x.first;
        }
            
      return 0;     
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
