---
title: "Rotate Array"
description: "Rotate the integer array k times"
categories
  - array
  - 2 pointer
---

### Question

> Given an array, rotate the array to the right by k steps, where k is non-negative.

```
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```

### Code [C++]

```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k %= n;
        for(int i=0;i<gcd(n,k);i++){
            int prev = i, next = (prev+k)%n;
            int temp = nums[i];
            while(next != i){
                int temp2 = nums[next];
                nums[next] = temp;
                temp = temp2;
                prev = next;
                next = (prev+k)%n;
            }
            nums[next] = temp;
        }
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
