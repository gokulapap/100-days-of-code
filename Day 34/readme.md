---
title: "Sum Tree"
description: "Return true if every node X in the tree has sum of its child"
categories:
  - trees
  - math
---

### Question

> Given a Binary Tree. Return true if, for every node X in the tree other than the leaves, its value is equal to the sum of its left subtree's value and its right subtree's value. Else return false.
> An empty tree is also a Sum Tree as the sum of an empty tree can be considered to be 0. A leaf node is also considered a Sum Tree.

```
Input:
    3
  /   \    
 1     2

Output: 1
Explanation:
The sum of left subtree and right subtree is
1 + 2 = 3, which is the value of the root node.
Therefore,the given binary tree is a sum tree.
```

### Code [C++]

```cpp
class Solution
{
    public:
    int Adder(Node* node)
    {
        if(!node)
            return 0;
        return Adder(node->left) + node->data + Adder(node->right);
    }
    bool isSumTree(Node* node) {

        if (!node || (!node->left && !node->right))
            return true;
 
        int lsum = Adder(node->left);
        int rsum = Adder(node->right);
 
        if ((node->data == lsum + rsum) && isSumTree(node->left) && isSumTree(node->right))
            return true;
 
        return false;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
