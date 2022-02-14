---
title: "Sum of Root to Leaf numbers"
description: "Return the total sum of all root-to-leaf numbers"
categories:
  - tree
  - recursion
---

### Question

> You are given the root of a binary tree containing digits from 0 to 9 only.
> Each root-to-leaf path in the tree represents a number.

 - For example, the root-to-leaf path 1 -> 2 -> 3 represents the number 123.

> Return the total sum of all root-to-leaf numbers. Test cases are generated so that the answer will fit in a 32-bit integer.
> A leaf node is a node with no children.

<br>
<img src="https://assets.leetcode.com/uploads/2021/02/19/num1tree.jpg"></img>
<br>

```
Input: root = [1,2,3]
Output: 25

Explanation:
The root-to-leaf path 1->2 represents the number 12.
The root-to-leaf path 1->3 represents the number 13.
Therefore, sum = 12 + 13 = 25.
```

### Code [C++]

```cpp
class Solution {
public:
    vector<string> nums;
    void traverse(TreeNode* root, string t)
    {
        if(!root->left && !root->right)
            nums.push_back(t);
        if(root->left)
            traverse(root->left, t+to_string(root->left->val));
        if(root->right)
            traverse(root->right, t+to_string(root->right->val));
    }
    
    int sumNumbers(TreeNode* root) {
        traverse(root, to_string(root->val));
        int sum = 0;
        for(auto x: nums)
        {
            sum += stoi(x);
        }
        
        return sum;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N logN)
