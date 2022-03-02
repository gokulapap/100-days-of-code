---
title: "Is Subsequence"
description: "check whether the given str is subsequence or not"
categories:
  - strings
---

### Question

> Given two strings s and t, return true if s is a subsequence of t, or false otherwise.
> A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

```
Example 1:

Input: s = "abc", t = "ahbgdc"
Output: true

Example 2:

Input: s = "axc", t = "ahbgdc"
Output: false
```

### Code [C++]

```cpp
class Solution {
public:
    bool isSubsequence(string s, string t) {
        if(s == "")
            return true;
        stack<char> chars;
        for(int i=s.size()-1; i>=0; i--)
            chars.push(s[i]);
        for(int i=0; i<t.size(); i++)
        {
            if(chars.empty())
                return true;
            if(chars.top() == t[i])
                chars.pop();
        }
        
        return chars.empty();
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
