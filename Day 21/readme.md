---
title: "Delete the Middle Node of a Linked List"
description: "Deleting the middle element and return the head"
categories:
  - linkedlist
  - median
---

### Question

> You are given the head of a linked list. Delete the middle node, and return the head of the modified linked list. The middle node of a linked list of size n is the ⌊n / 2⌋th node from the start using 0-based indexing, where ⌊x⌋ denotes the largest integer less than or equal to x.

> For n = 1, 2, 3, 4, and 5, the middle nodes are 0, 1, 1, 2, and 2, respectively.

<br>
<img src="https://assets.leetcode.com/uploads/2021/11/16/eg1drawio.png"></img>
<br>

```
Input: head = [1,3,4,7,1,2,6]
Output: [1,3,4,1,2,6]
Explanation:
The above figure represents the given linked list. The indices of the nodes are written below.
Since n = 7, node 3 with value 7 is the middle node, which is marked in red.
We return the new list after removing this node. 
```

### Code [C++]

```cpp
class Solution {
public:
    ListNode* deleteMiddle(ListNode* head) {
        ListNode* fast = head, *slow = head, *prev=NULL;
        
        if(!head->next)
            return NULL;
        
        while(fast && fast->next)
        {
            fast = fast->next->next;
            prev = slow;
            slow = slow->next;
        }

        prev->next = slow->next;  
        return head;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
