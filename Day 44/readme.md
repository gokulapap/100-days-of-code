---
title: "Swap nodes in Pairs"
description: "swap every two adjacent nodes and return its head"
categories:
  - linkedlist
  - swap
---

### Question

> Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

<br>
<img src="https://assets.leetcode.com/uploads/2020/10/03/swap_ex1.jpg">
<br>

``` 
Input: head = [1,2,3,4]
Output: [2,1,4,3]
```

### Code [C++]

```cpp
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        if(!head or !head->next)
            return head;
        ListNode* temp;
        temp = head->next;
        head->next = swapPairs(head->next->next);
        temp->next = head;
        
        return temp;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
