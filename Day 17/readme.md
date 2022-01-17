---
title: "Flood Fill"
description: "You should perform a flood fill on the image starting from pixel[sr][sc] with newcolor"
categories:
  - dfs
  - graph
---

### Question

> An image is represented by an m x n integer grid image where image[i][j] represents the pixel value of the image.You are also given three integers sr, sc, and newColor. You should perform a flood fill on the image starting from the pixel image[sr][sc]. To perform a flood fill, consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with newColor.

> Return the modified image after performing the flood fill.

<br>
<img src="https://assets.leetcode.com/uploads/2021/06/01/flood1-grid.jpg" width=450px height=250px></img>
<br>

```
Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, newColor = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
Explanation: From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.
```

### Code [C++]

```cpp
class Solution {
public:
    void traverse(vector<vector<int>>& image, int row, int col, int pixel, int ncolor)
    {
        if(row < 0 || row >= image.size() || col < 0 || col >= image[0].size())
            return;
        if(image[row][col] != pixel)
            return;

        image[row][col] = ncolor;
        
        traverse(image, row+1, col, pixel, ncolor);
        traverse(image, row-1, col, pixel, ncolor);
        traverse(image, row, col+1, pixel, ncolor);
        traverse(image, row, col-1, pixel, ncolor);
        
    }
    
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor) {
        int pixel = image[sr][sc];
        if(newColor == pixel)
            return image;
        traverse(image, sr, sc, pixel, newColor);
        
        return image;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
