---
title: "Linked List Cycle"
description: "Given the head of the Linkedlist return the node where the cycle begins"
categories:
  - linkedlist
  - cycle
---

### Question

> Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

> Do not modify the linked list.

<br>
<img src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png"></img>
<br>

```
Input: head = [3,2,0,-4], pos = 1
Output: tail connects to node index 1
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

### Code [C++]

```cpp
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        vector<ListNode*> vis;
        while(head)
        {
            if(count(vis.begin(), vis.end(), head) > 0)
                return *find(vis.begin(), vis.end(), head);
            vis.push_back(head);
            head = head->next;
        }
        return head;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
