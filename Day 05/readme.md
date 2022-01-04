---
title: "Number of Islands"
description: "Find number of islands that is surrounded by water"
categories:
  - Coding
---

### Question

> Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

### Code [CPP]

```cpp
class Solution {
public:
    void traversal(vector<vector<char>>& grid, int row, int col)
    {
        if(row<0 || row>=grid.size() || col<0 || col>=grid[0].size())
            return;
        if(grid[row][col] == '0')
            return;
        
        grid[row][col] = '0';
        traversal(grid, row+1, col);
        traversal(grid, row-1, col);
        traversal(grid, row, col+1);
        traversal(grid, row, col-1);
        
    }

    int numIslands(vector<vector<char>>& grid) {
        int islandCount = 0;
        for(int i=0; i<grid.size(); i++)
        {
            for(int j=0; j<grid[0].size(); j++)
            {
                if(grid[i][j] == '1')
                {
                    islandCount++;
                    traversal(grid, i, j);
                }
            }
        }
        
        return islandCount;
    }
};
```


> Time Complexity = O(4^N)

> Space Complexity = O(1)
