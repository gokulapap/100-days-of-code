---
title: " Find whether path exists"
description: "Check whether there is a path possible from the source to destination"
categories:
  - Coding
---

### Question

> Given a grid of size n*n filled with 0, 1, 2, 3. Check whether there is a path possible from the source to destination. You can traverse up, down, right and left.
> The description of cells is as follows:

```
    A value of cell 1 means Source.
    A value of cell 2 means Destination.
    A value of cell 3 means Blank cell.
    A value of cell 0 means Wall.
```

> Note: There are only a single source and a single destination.

### Code [CPP]

```cpp
class Solution
{
    public:
    bool traverse(vector<vector<int>>& grid, int srow, int scol, int drow, int dcol)
    {
        if(srow < 0 || srow >= grid.size())
            return false;
        if(scol < 0 || scol >= grid[0].size())
            return false;
        if(srow == drow && scol == dcol)
            return true;
        if(grid[srow][scol] == 0)
            return false;
        grid[srow][scol] = 0;
        return traverse(grid, srow, scol-1, drow, dcol) || traverse(grid, srow, scol+1, drow, dcol) || traverse(grid, srow+1, scol, drow, dcol) ||  traverse(grid, srow-1, scol, drow, dcol);
    }
    
    bool is_Possible(vector<vector<int>>& grid) 
    {
        int srcR = 0, srcC = 0, destR = 0, destC = 0;
        for(int i=0; i<grid.size(); i++)
        {
            for(int j=0; j<grid[0].size(); j++)
            {
                if(grid[i][j] == 1)
                {
                    srcR = i;
                    srcC = j;
                }
                if(grid[i][j] == 2)
                {
                    destR = i;
                    destC = j;
                }
            }
        }
        
        return traverse(grid, srcR, srcC, destR, destC);
    }
};
```


> Time Complexity = O(N^2)

> Space Complexity = O(1)
