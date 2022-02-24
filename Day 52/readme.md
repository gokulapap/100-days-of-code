---
title: "Sort List"
description: "Sort the given Linkedlist"
categories:
  - sorting
  - linkedlist
---

### Question

> Given the head of a linked list, return the list after sorting it in ascending order.

<br>
<img src="https://assets.leetcode.com/uploads/2020/09/14/sort_list_1.jpg">
<br>

```
Input: head = [4,2,1,3]
Output: [1,2,3,4]
```

### Code [C++]

```cpp
class Solution {
public:
    ListNode* sortList(ListNode* head) {
        if(!head)
            return head;
        vector<int> nums;
        while(head)
        {
            nums.push_back(head->val);
                head = head -> next;
        }      
        sort(nums.begin(), nums.end());        
        head = new ListNode(nums[0]);
        ListNode* temp = head;
        
        for(int i=1; i<nums.size(); i++)
        {
            temp->next = new ListNode(nums[i]);
            temp = temp->next;
        }
        return head;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
