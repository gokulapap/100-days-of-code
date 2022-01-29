---
title: "Sum of Root to Leaf Binary numbers"
description: "sum of binary numbers from root to leaf"
categories:
  - trees
  - dfs
---

### Question

> You are given the root of a binary tree where each node has a value 0 or 1. Each root-to-leaf path represents a binary number starting with the most significant bit.
 
   - For example, if the path is 0 -> 1 -> 1 -> 0 -> 1, then this could represent 01101 in binary, which is 13.

> For all leaves in the tree, consider the numbers represented by the path from the root to that leaf. Return the sum of these numbers.
> The test cases are generated so that the answer fits in a 32-bits integer.

### Code [C++]

```cpp
class Solution {
public:
    vector<string> nums;
    void traverse(TreeNode* root, string t)
    {
        if(!root->left && !root->right)
        {
            nums.push_back(t);
            return;
        }
        if(root->left)
            traverse(root->left, t+to_string(root->left->val));
        if(root->right)
            traverse(root->right, t+to_string(root->right->val));
    }  
    int BinaryToDecimal(string n)
    {
        int bin = 0;
        int p = 0;
        for(int i=n.size()-1; i>=0; i--)
        {
            bin += pow(2, p) * stoi(n.substr(i,1));
            p++;
        }
        
        return bin;
    }
    
    int sumRootToLeaf(TreeNode* root) {
        traverse(root, to_string(root->val));
        int sum = 0;
        for(auto x: nums)
        {
            sum += BinaryToDecimal(x);
        }
        
        return sum;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
