---
title: "Kth smallest element"
description: "find the Kth smallest element in the given array"
categories:
  - Array
  - Math
---

### Question

> Given an array arr[] and an integer K where K is smaller than size of array, the task is to find the Kth smallest element in the given array. It is given that all array elements are distinct.

```
Input:
N = 6
arr[] = 7 10 4 3 20 15
K = 3
Output : 7
Explanation :
3rd smallest element in the given 
array is 7.
```

### Code [C++]

```cpp
class Solution{
    public:
    int kthSmallest(int arr[], int l, int r, int k) {
        priority_queue <int, vector<int>, greater<int>> pq;
        for(int i=0; i<=r; i++)
        {
            pq.push(arr[i]);
        }
        while(k-1)
        {
            pq.pop();
            k--;
        }
        return pq.top();
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
