---
title: "Word Search"
description: "Finding whether the given word is present in the grid"
categories:
  - Coding
---

### Question

> Given an m x n grid of characters board and a string word, return true if word exists in the grid. The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

<img src="https://assets.leetcode.com/uploads/2020/11/04/word2.jpg"/>

```
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
Output: true
```

### Code [CPP]

```cpp
class Solution {
public:
    bool traverse(vector<vector<char>>& board, int i, int j, int index, string word)
    {
        if(i<0 || i>=board.size() || j<0 || j>=board[0].size())
            return false;
        if(board[i][j] != word[index])
            return false;
        if(board[i][j] == '&')
            return false;
        if(index == word.size()-1)
            return true;
        
        char temp = board[i][j];
        board[i][j] = '&';
        index = index + 1;
        bool ans = traverse(board, i+1, j, index, word) || traverse(board, i-1, j, index, word) || traverse(board, i, j+1, index, word) || traverse(board, i, j-1, index, word);
        
        board[i][j] = temp;
        return ans;
    }
    
    // main function
    bool exist(vector<vector<char>>& board, string word) {
        bool out;
        for(int i=0; i<board.size(); i++)
        {
            for(int j=0; j<board[0].size(); j++)
            {
                if(board[i][j] == word[0])
                {
                    if(traverse(board, i, j, 0, word))
                        return true;
                }
            }
        }
        
        return false;
    }
};
```


> Time Complexity = O(N*4N)

> Space Complexity = O(1)
