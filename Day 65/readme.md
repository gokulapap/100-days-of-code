---
title: "Remove duplicates from sortedlist 2"
description: "delete all nodes that have duplicate numbers"
categories:
  - linkedlist
  - array
---

### Question

> Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well.

<br>
<img src="https://assets.leetcode.com/uploads/2021/01/04/linkedlist1.jpg">
<br>

```
Input: head = [1,2,3,3,4,4,5]
Output: [1,2,5]
```

### Code [C++]

```cpp
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if(!head)
            return 0;
        if(!head -> next)
            return head;
        
        int val = head->val;
        ListNode *temp = head->next;
        
        if(temp->val != val)
        {
            head->next = deleteDuplicates(temp);
            return head;
        }
        else
        {
           while(temp && temp->val == val)
            {
                ListNode *p = temp;
                temp = temp->next;
                delete p;
            }
            return deleteDuplicates(temp);
        }
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
