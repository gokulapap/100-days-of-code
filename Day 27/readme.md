---
title: "Leaf-Similar Trees"
description: "return true if leaves of both trees same"
categories:
  - trees
  - dfs
---

### Question

> Consider all the leaves of a binary tree, from left to right order, the values of those leaves form a leaf value sequence. Two binary trees are considered leaf-similar if their leaf value sequence is the same.

> Return true if and only if the two given trees with head nodes root1 and root2 are leaf-similar.

<br>
<img src="https://assets.leetcode.com/uploads/2020/09/03/leaf-similar-1.jpg" height=300px width=430px></img>
<br>

```
Input: root1 = [3,5,1,6,2,9,8,null,null,7,4], root2 = [3,5,1,6,7,4,2,null,null,null,null,null,null,9,8]
Output: true
```

### Code [C++]

```cpp
class Solution {
public:
    bool leafSimilar(TreeNode* root1, TreeNode* root2) {
        vector<int> leaves1;
        vector<int> leaves2;
        dfs(root1, leaves1);
        dfs(root2, leaves2);

        return leaves1 == leaves2;
    }

    void dfs(TreeNode* node, vector<int>& leaves) {
        if (node == NULL) 
            return;
        if (!node->left && !node->right)
            leaves.push_back(node->val);
        dfs(node->left, leaves);
        dfs(node->right, leaves);
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N+M)
