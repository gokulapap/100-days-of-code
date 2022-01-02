---
title: "Dutch national flag problem"
description: "Sort 0's, 1's, 2's without inbuilt functions"
categories:
  - Coding
---

### Question

> Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively. You must solve this problem without using the library's sort function.

### Code [CPP]

```cpp
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int low = 0, high = nums.size()-1, mid = 0;
        while(mid <= high)
        {
            if(nums[mid] == 0)
            {
                swap(nums[low], nums[mid]);
                low++;
                mid++;
            }
            else if(nums[mid] == 1)
                mid++;
            else
            {
                swap(nums[mid], nums[high]);
                high--;
            }
        }
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
