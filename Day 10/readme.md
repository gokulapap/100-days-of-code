---
title: "Max Area of Island"
description: "finding the maximum area of island surrounded by water"
categories:
  - graph, dfs
---

### Question

> You are given an m x n binary matrix grid. An island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water. The area of an island is the number of cells with a value 1 in the island.

> Return the maximum area of an island in grid. If there is no island, return 0.

<img src="https://assets.leetcode.com/uploads/2021/05/01/maxarea1-grid.jpg"></img>

```
Input: grid = [[0,0,1,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,1,1,0,1,0,0,0,0,0,0,0,0],[0,1,0,0,1,1,0,0,1,0,1,0,0],[0,1,0,0,1,1,0,0,1,1,1,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,0,0,0,0,0,0,1,1,0,0,0,0]]
Output: 6
Explanation: The answer is not 11, because the island must be connected 4-directionally.
```

### Code [CPP]

```cpp
class Solution {
public:
    int maxArea = 0;
    int currArea = 0;
   
    void traverse(vector<vector<int>>& grid, int row, int col)
    {
        if(row < 0 || row >= grid.size() || col< 0 || col >=grid[0].size())
            return;
        if(grid[row][col] == 0)
            return;
        
        grid[row][col] = 0;
        currArea++;
        traverse(grid, row+1, col);
        traverse(grid, row-1, col);
        traverse(grid, row, col+1);
        traverse(grid, row, col-1);
    }
    
    int maxAreaOfIsland(vector<vector<int>>& grid) {
        for(int i=0; i<grid.size(); i++)
        {
            for(int j=0; j<grid[0].size(); j++)
            {
                if(grid[i][j] == 1)
                {
                    currArea = 0;
                    traverse(grid, i, j);
                    if(currArea > maxArea)
                    {
                        maxArea = currArea;
                    }
                }
            }
        }
        
        return maxArea;
    }
};
```


> Time Complexity = O(N)

> Space Complexity = O(1)
