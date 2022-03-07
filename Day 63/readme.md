---
title: "Merge Two Sorted Lists"
description: "Merge the given two sorted linkedlists"
categories:
  - linkedlist
  - sorting
---

### Question

> You are given the heads of two sorted linked lists list1 and list2. Merge the two lists in a one sorted list. The list should be made by splicing together the nodes of the first two lists.
> Return the head of the merged linked list.

<br>
<img src="https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg">
<br>

```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

### Code [C++]

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if(!l1)
            return l2;
        if(!l2)
            return l1;
        ListNode *ans = NULL,*temp = NULL;
        while(l1 && l2)
        {
            if(l1->val < l2->val)
            {
                if(!ans)
                {
                    ans = new ListNode(l1->val);
                    temp = ans;
                }
                else
                {
                    temp->next = new ListNode(l1->val);
                    temp = temp->next;
                }
                l1 = l1->next;
            }
            else
            {
                if(!ans)
                {
                    ans = new ListNode(l2->val);
                    temp = ans;
                }
                else
                {
                    temp->next = new ListNode(l2->val);
                    temp = temp->next;
                }   
                l2 = l2->next;
            }
            
            if(!l1)
            {
                while(l2)
                {
                    temp->next = new ListNode(l2->val);
                    temp = temp->next;
                    l2 = l2->next;
                }
                break;
            }
            if(!l2)
            {
                while(l1)
                {
                    temp->next = new ListNode(l1->val);
                    temp = temp->next;
                    l1 = l1->next;
                }
                break;
            }
        }
        return ans;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
