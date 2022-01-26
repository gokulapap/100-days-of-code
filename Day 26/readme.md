---
title: "Path sum of Binary tree"
description: "if root-to-leaf paths equal to target sum return that vector"
categories:
  - trees
  - dfs
---

### Question

> Given the root of a binary tree and an integer targetSum, return all root-to-leaf paths where the sum of the node values in the path equals targetSum. Each path should be returned as a list of the node values, not node references.

> A root-to-leaf path is a path starting from the root and ending at any leaf node. A leaf is a node with no children.

<br>
<img src="https://assets.leetcode.com/uploads/2021/01/18/pathsumii1.jpg" height=400px width=430px></img>
<br>

```
Input: root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
Output: [[5,4,11,2],[5,8,4,5]]
Explanation: There are two paths whose sum equals targetSum:
5 + 4 + 11 + 2 = 22
5 + 8 + 4 + 5 = 22
```

### Code [C++]

```cpp
class Solution {
public:
    vector<vector<int>> ans;
    void traverse(TreeNode* root, vector<int> t, int target)
    {
        if(!root->left && !root->right)
        {
            int sum = 0;
            for(auto x: t)
                sum += x;
            if(sum == target)
                ans.push_back(t);
            return;
        }
        if(root->left)
        {
            vector<int> temp = t;
            temp.push_back(root->left->val);
            traverse(root->left, temp, target);
        }
        if(root->right)
        {
            vector<int> temp = t;
            temp.push_back(root->right->val);
            traverse(root->right, temp, target);
        }
    }
    vector<vector<int>> pathSum(TreeNode* root, int targetSum) {
        if(!root)
            return ans;
        traverse(root, {root->val}, targetSum);
        return ans;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
