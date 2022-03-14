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
		ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
			if (l1 == NULL and l2 == NULL) return NULL;
			else if (l1 == NULL) return l2; 
			else if (l2 == NULL) return l1; 

			int a = l1->val + l2->val;
			ListNode *p = new ListNode(a % 10);
			p->next = addTwoNumbers(l1->next,l2->next);
			if (a >= 10) 
                p->next = addTwoNumbers(p->next, new ListNode(1));
			return p;
		}
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
