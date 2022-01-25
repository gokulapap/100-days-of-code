---
title: "Valid Mountain Array"
description: "Return true if its valid mountain array"
categories:
  - array
---

### Question

> Given an array of integers arr, return true if and only if it is a valid mountain array.
> Recall that arr is a mountain array if and only if:
```
arr.length >= 3
There exists some i with 0 < i < arr.length - 1 such that:
   arr[0] < arr[1] < ... < arr[i - 1] < arr[i]
   arr[i] > arr[i + 1] > ... > arr[arr.length - 1]
```
<br>
<img src="https://assets.leetcode.com/uploads/2019/10/20/hint_valid_mountain_array.png"></img>
<br>

```
Example 1:

Input: arr = [2,1]
Output: false

Example 2:

Input: arr = [3,5,5]
Output: false
```

### Code [C++]

```cpp
class Solution {
public:
    bool validMountainArray(vector<int>& arr) {
        if(arr.size() < 3)
            return false;
        int l = 0;
        int r = arr.size() - 1;
        while(l + 1 < arr.size() - 1 && arr[l] < arr[l + 1])
            l++;
        while(r - 1 > 0 && arr[r] < arr[r - 1])
            r--;
        
        return l == r;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
