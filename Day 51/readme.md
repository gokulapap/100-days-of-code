---
title: "Average of levels in Binary tree"
description: "return the average value of the nodes on each level"
categories:
  - trees
  - dfs
---

### Question

> Given the root of a binary tree, return the average value of the nodes on each level in the form of an array. Answers within 10-5 of the actual answer will be accepted. 

<br>
<img src="https://assets.leetcode.com/uploads/2021/03/09/avg1-tree.jpg">
<br>

```
Input: root = [3,9,20,null,null,15,7]
Output: [3.00000,14.50000,11.00000]
Explanation: The average value of nodes on level 0 is 3, on level 1 is 14.5, and on level 2 is 11.
Hence return [3, 14.5, 11].
```

### Code [C++]

```cpp
class Solution {
public:
   vector<double> averageOfLevels(TreeNode* root) {
        vector<double> result;
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty()) {
            long temp = 0;
            int s = q.size();
            for(int i=0; i<s; i++) {
                TreeNode* t = q.front();
                q.pop();
                if(t->left)
                    q.push(t->left);
                if(t->right)
                    q.push(t->right);
                temp += t->val;
            }
            result.push_back((double)temp/s);
        }
        return result;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
