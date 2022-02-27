---
title: "Maximum Width of Binary Tree"
description: "Return the maximum width of the given tree"
categories:
  - comparing
  - strings
---

### Question

> Given the root of a binary tree, return the maximum width of the given tree.
> The maximum width of a tree is the maximum width among all level.
> The width of one level is defined as the length between the end-nodes (the leftmost and rightmost non-null nodes), where the null nodes between the end-nodes are also counted into the length calculation.

<br>
<img src="https://assets.leetcode.com/uploads/2021/05/03/width1-tree.jpg">
<br>

```
Input: root = [1,3,2,5,3,null,9]
Output: 4
Explanation: The maximum width existing in the third level with the length 4 (5,3,null,9).
```

### Code [C++]

```cpp
class Solution {
public:
    int widthOfBinaryTree(TreeNode* root) {
        int width = 0;
        queue<pair<TreeNode*, int>>q;
        q.push({root, 0});
        while(!q.empty()){
            int n = q.size();
            int max_index = INT_MIN, min_index = INT_MAX;
            while(n--){
                TreeNode* tmp = q.front().first;
                int dist = q.front().second;
                q.pop();
                max_index = max(max_index, dist);
                min_index = min(min_index, dist);
                if(tmp->left){
                    q.push({tmp->left, (long long)2 * dist + 1});
                }
                if(tmp->right){
                    q.push({tmp->right, (long long)2 * dist + 2});
                }
            }
            width = max(width, max_index - min_index + 1);
        }
        return width;      
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
