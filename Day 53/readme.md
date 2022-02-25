---
title: "Compare version Number"
description: "Given two version numbers, version1 and version2, compare them"
categories:
  - comparing
  - strings
---

### Question

> Given two version numbers, version1 and version2, compare them.
> Version numbers consist of one or more revisions joined by a dot '.'. Each revision consists of digits and may contain leading zeros. Every revision contains at least one character. Revisions are 0-indexed from left to right, with the leftmost revision being revision 0, the next revision being revision 1, and so on. For example 2.5.33 and 0.1 are valid version numbers.
> To compare version numbers, compare their revisions in left-to-right order. Revisions are compared using their integer value ignoring any leading zeros. This means that revisions 1 and 001 are considered equal. If a version number does not specify a revision at an index, then treat the revision as 0. For example, version 1.0 is less than version 1.1 because their revision 0s are the same, but their revision 1s are 0 and 1 respectively, and 0 < 1.

> Return the following:

 -  If version1 < version2, return -1.
 -  If version1 > version2, return 1.
 -  Otherwise, return 0.

```
Example 1:

Input: version1 = "1.01", version2 = "1.001"
Output: 0
Explanation: Ignoring leading zeroes, both "01" and "001" represent the same integer "1".

Example 2:

Input: version1 = "1.0", version2 = "1.0.0"
Output: 0
Explanation: version1 does not specify revision 2, which means it is treated as "0".

Example 3:

Input: version1 = "0.1", version2 = "1.1"
Output: -1
Explanation: version1's revision 0 is "0", while version2's revision 0 is "1". 0 < 1, so version1 < version2.
```

### Code [C++]

```cpp
class Solution {
public:
int compareVersion(string version1, string version2) {
        stringstream ss1(version1), ss2(version2);
        string line;
        vector<int> v1, v2;
        while(getline(ss1, line, '.'))
            v1.push_back(stoi(line));
        while(getline(ss2, line, '.'))
            v2.push_back(stoi(line));
        while(v1.size() < v2.size())
            v1.push_back(0);
        while(v2.size() < v1.size())
            v2.push_back(0);                
        for(int i = 0; i < v1.size(); i++)
            if(v1[i] != v2[i])
                return v1[i] > v2[i] ? 1 : -1;            
        return 0;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
