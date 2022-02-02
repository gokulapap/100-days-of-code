---
title: "Minimum number of steps to make anagram"
description: "find minimum number of steps to make anagram"
categories:
  - string
  - hash table
---

### Question

> You are given two strings of the same length s and t. In one step you can choose any character of t and replace it with another character. Return the minimum number of steps to make t an anagram of s.

> An Anagram of a string is a string that contains the same characters with a different (or the same) ordering.

```
Input: s = "bab", t = "aba"
Output: 1
Explanation: Replace the first 'a' in t with b, t = "bba" which is anagram of s.
```

### Code [C++]

```cpp
class Solution {
public:
    int minSteps(string s, string t) {
        unordered_map<char,int> m;
        int sum=0;
        
        for(auto i: s)
            m[i]++;
        for(auto i: t)
            m[i]--;
        for(auto i: m)
        {
            if(i.second < 0)
                sum += abs(i.second);
        }

        return sum;
    }
};
```

> Time Complexity = O(N+M)

> Space Complexity = O(N)
