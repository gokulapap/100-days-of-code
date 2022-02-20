---
title: "Remove Covered Intervals"
description: "Return the number of remaining intervals"
categories:
  - sorting
  - array
---

### Question

> Given an array intervals where intervals[i] = [li, ri] represent the interval [li, ri), remove all intervals that are covered by another interval in the list.
> The interval [a, b) is covered by the interval [c, d) if and only if c <= a and b <= d.

> Return the number of remaining intervals.

```
Example 1:

Input: intervals = [[1,4],[3,6],[2,8]]
Output: 2
Explanation: Interval [3,6] is covered by [2,8], therefore it is removed.

Example 2:

Input: intervals = [[1,4],[2,3]]
Output: 1
```

### Code [C++]

```cpp
class Solution {
public:
    int removeCoveredIntervals(vector<vector<int>>& intervals) {
        sort(intervals.begin(),intervals.end());        
        int x1 = intervals[0][0];
        int x2 = intervals[0][1];
		int res = 1;  
        for(int i=1; i<intervals.size(); ++i)
        {
            if(intervals[i][0] > x1 && intervals[i][1] > x2)
                ++res;
            if(intervals[i][1] > x2)
            {
                x1 = intervals[i][0];
                x2 = intervals [i][1];
            }
        }
        return res;       
    }

}; 
```

> Time Complexity = O(N)

> Space Complexity = O(1)
