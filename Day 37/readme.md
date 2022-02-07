---
title: "Zigzag Conversion"
description: "return zigzag pattern of a given string"
categories:
  - string
  - zigzag
---

### Question

> The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```
> And then read line by line: "PAHNAPLSIIGYIR"

> Write the code that will take a string and make this conversion given a number of rows

```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"

Example 2:

Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"

Explanation:

P     I    N
A   L S  I G
Y A   H R
P     I

```

### Code [C++]

```cpp
class Solution {
public:
    string convert(string s, int numRows) {

        if (numRows == 1) return s;

        string ans;
        int n = s.size();
        int cycleLen = 2 * numRows - 2;

        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j + i < n; j += cycleLen) {
                ans += s[j + i];
                if (i != 0 && i != numRows - 1 && j + cycleLen - i < n)
                    ans += s[j + cycleLen - i];
            }
        }
        return ans;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
