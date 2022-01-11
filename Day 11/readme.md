---
title: "N-Queens"
description: "Placing N queens in NxN chess board without attacking other queen"
categories:
  - graph
  - dfs
---

### Question

> The n-queens puzzle is the problem of placing n queens on an n x n chessboard such that no two queens attack each other. Given an integer n, return all distinct solutions to the n-queens puzzle. You may return the answer in any order.

> Each solution contains a distinct board configuration of the n-queens' placement, where 'Q' and '.' both indicate a queen and an empty space, respectively.

<br>
<img src="https://assets.leetcode.com/uploads/2020/11/13/queens.jpg" height=400px width=800px></img>
<br>

```
Input: n = 4
Output: [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
Explanation: There exist two distinct solutions to the 4-queens puzzle as shown above
```

### Code [CPP]

```cpp
class Solution {
public:
    vector<vector<string>> result;
    
    void solver(vector<string>& board, int row)
    {
        if(row == board.size())
        {
            result.push_back(board);
            return;
        }
        
        for(int col=0; col < board.size(); col++)
        {
            if(isValid(board, row, col))
            {
                board[row][col] = 'Q';
                solver(board, row+1);
                board[row][col] = '.';
            }
        } 
    }
    
    bool isValid(vector<string>& board, int row, int col)
    {
        int rowval = row;
        int colval = col;
        while(row >= 0)
        {
            if(board[row][col] == 'Q')
                return false;
            row--;
        }
        row = rowval;
        while(row >= 0 && col >= 0)
        {
            if(board[row][col] == 'Q')
                return false;
            row--;
            col--;
        }
        row = rowval;
        col = colval;
        while(row >=0 && col < board.size())
        {
            if(board[row][col] == 'Q')
                return false;
            row--;
            col++;
        }
        
        return true;
    }
    
    vector<vector<string>> solveNQueens(int n) {
        if(n <= 0) return {{}};
        vector<string> board(n, string(n, '.'));
        solver(board, 0);
        return result;
    }
};
```


> Time Complexity = O(N^2)

> Space Complexity = O(N)
