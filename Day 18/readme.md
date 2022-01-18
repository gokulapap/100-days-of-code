---
title: "Validate Binary Search Tree"
description: "Given the root of a binary tree, determine if it is a valid binary search tree BST"
categories:
  - bst
  - tree
---

### Question

> Given the root of a binary tree, determine if it is a valid binary search tree (BST).
> A valid BST is defined as follows:

- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.

<br>
<img src="https://assets.leetcode.com/uploads/2020/12/01/tree2.jpg"></img>
<br>

```
Input: root = [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4
```

### Code [C++]

```cpp
class Solution {
public:
    bool isValidBST(TreeNode* root) {
        return isValid(root, NULL, NULL);
    }
    
    bool isValid(TreeNode* root, int* lower, int* upper)
    {
        if(!root)
            return true;
        if(upper && root->val >= *upper)
            return false;
        if(lower && root->val <= *lower)
            return false;
        
        return isValid(root -> left, lower, &(root -> val)) && isValid(root -> right, &(root -> val), upper);
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
