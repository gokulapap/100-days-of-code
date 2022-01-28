---
title: "Delete Leaves with a Given target"
description: "delete a leaf node that matches the target value"
categories:
  - trees
  - dfs
---

### Question

> Given a binary tree root and an integer target, delete all the leaf nodes with value target.

> Note that once you delete a leaf node with value target, if its parent node becomes a leaf node and has the value target, it should also be deleted (you need to continue doing that until you cannot).

<br>
<img src="https://assets.leetcode.com/uploads/2020/01/09/sample_1_1684.png" height=300px width=520px></img>
<br>

```
Input: root = [1,2,3,2,null,2,4], target = 2
Output: [1,null,3,null,4]
Explanation: Leaf nodes in green with value (target = 2) are removed (Picture in left). 
After removing, new nodes become leaf nodes with value (target = 2) (Picture in center).
```
 

### Code [C++]

```cpp
class Solution {
public:
    TreeNode* removeLeafNodes(TreeNode* root, int target) 
    {
        if (root->left)     
        {
            TreeNode* lNode = removeLeafNodes(root->left, target);     
            root->left = lNode;
        }
        if (root->right)   
        {
            TreeNode* rNode = removeLeafNodes(root->right, target);     
            root->right = rNode;
        }
        if (root->val == target && !root->left && !root->right)   
        {
            return NULL;
        }
        
        return root;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
