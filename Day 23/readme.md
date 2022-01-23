---
title: "Sequential digits"
description: "Find all the sequential digits in the given range"
categories:
  - math
  - enumeration
---

### Question

> An integer has sequential digits if and only if each digit in the number is one more than the previous digit.

> Return a sorted list of all the integers in the range [low, high] inclusive that have sequential digits.

```
Example 1:

Input: low = 100, high = 300
Output: [123,234]

Example 2:

Input: low = 1000, high = 13000
Output: [1234,2345,3456,4567,5678,6789,12345]
```

### Code [C++]

```cpp
class Solution {
public:
    vector<int> sequentialDigits(int low, int high) {      
        vector<int> ans;
        int sum;
        for(int i=1;i<=9;i++)
        {
            sum=0;
            for(int j=i;j<=9;j++)
            {
               sum=sum*10+j;   
                if(sum>=low && sum<=high)
                {
                    ans.push_back(sum);
                }
            }
        }
        sort(ans.begin(),ans.end());
        return ans;
        
    }
};
```

> Time Complexity = O(9^2)

> Space Complexity = O(N)
