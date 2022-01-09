---
title: "Maximum Twin Sum of a Linked List"
description: "finding the maximum of twin sum in a linkedlist"
categories:
  - linked list
---

### Question

> In a linked list of size n, where n is even, the ith node (0-indexed) of the linked list is known as the twin of the (n-1-i)th node, if 0 <= i <= (n / 2) - 1.
> For example, if n = 4, then node 0 is the twin of node 3, and node 1 is the twin of node 2. These are the only nodes with twins for n = 4.
> The twin sum is defined as the sum of a node and its twin.

> Given the head of a linked list with even length, return the maximum twin sum of the linked list.

<img src="https://assets.leetcode.com/uploads/2021/12/03/eg1drawio.png"></img>

```
Input: head = [5,4,2,1]
Output: 6
Explanation:
Nodes 0 and 1 are the twins of nodes 3 and 2, respectively. All have twin sum = 6.
There are no other nodes with twins in the linked list.
Thus, the maximum twin sum of the linked list is 6.
```

### Code [CPP]

```cpp
class Solution {
public:
    int pairSum(ListNode* head) {
        int maxsum = 0;
        vector<int> nums;
        while(head)
        {
            nums.push_back(head->val);
            head = head->next;
        }
        
        int n = nums.size()-1;
        
        for(int i=0; i<nums.size()/2; i++)
        {
            int sum = 0;
            sum = nums[i] + nums[n-i];
            if(sum > maxsum)
                maxsum = sum;
        }
     
        return maxsum;
    }
};
```


> Time Complexity = O(2N)

> Space Complexity = O(N)
