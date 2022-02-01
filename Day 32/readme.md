---
title: "Odd Even Linkedlist"
description: "group nodes with odd and even indices together"
categories:
  - linkedlist
---

### Question

> Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.
> The first node is considered odd, and the second node is even, and so on.

> Note that the relative order inside both the even and odd groups should remain as it was in the input.
> You must solve the problem in O(1) extra space complexity and O(n) time complexity.

<br>
<img src="https://assets.leetcode.com/uploads/2021/03/10/oddeven-linked-list.jpg" width=430px height=350px></img>
<br>

```
Input: head = [1,2,3,4,5]
Output: [1,3,5,2,4]
```

### Code [C++]

```cpp
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        if(!head)
            return head;
        ListNode* odd = head, *even = head->next, *temp = even;
        while(even && even->next)
        {
            odd->next = even->next;
            odd = odd->next;
            even->next = odd->next;
            even = even->next;
        }
        odd->next = temp;
        
        return head;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
