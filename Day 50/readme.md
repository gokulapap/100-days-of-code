---
title: "Excel sheet column number"
description: "In an Excel sheet, return its corresponding column number"
categories:
  - sorting
  - string
---

### Question

> Given a string columnTitle that represents the column title as appear in an Excel sheet, return its corresponding column number.

```
For example:

A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
...
```

```
Example 1:

Input: columnTitle = "A"
Output: 1

Example 2:

Input: columnTitle = "AB"
Output: 28

Example 3:

Input: columnTitle = "ZY"
Output: 701
```

### Code [C++]

```cpp
class Solution {
public:
    int titleToNumber(string columnTitle) {
        int result = 0;
        for(char c : columnTitle)
        {
            int d = c - 'A' + 1;
            result = result * 26 + d;
        }
        return result;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
