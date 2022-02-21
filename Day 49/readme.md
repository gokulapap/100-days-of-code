---
title: "Sort Characters by Frequency"
description: "Return the sorted string based on frequency"
categories:
  - sorting
  - string
---

### Question

> Given a string s, sort it in decreasing order based on the frequency of the characters. The frequency of a character is the number of times it appears in the string.
> Return the sorted string. If there are multiple answers, return any of them.

```
Example 1:

Input: s = "tree"
Output: "eert"
Explanation: 'e' appears twice while 'r' and 't' both appear once.
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.

Example 2:

Input: s = "cccaaa"
Output: "aaaccc"
Explanation: Both 'c' and 'a' appear three times, so both "cccaaa" and "aaaccc" are valid answers.
Note that "cacaca" is incorrect, as the same characters must be together.

Example 3:

Input: s = "Aabb"
Output: "bbAa"
Explanation: "bbaA" is also a valid answer, but "Aabb" is incorrect.
Note that 'A' and 'a' are treated as two different characters.
```

### Code [C++]

```cpp
class Solution {
public:
    string frequencySort(string s) {
        priority_queue<pair<int, char>> pq;
        map<char, int> counter;
        for(auto x: s)
            counter[x]++;
        for(auto x: counter)
            pq.push({x.second, x.first});

        string ans;
        while(!pq.empty())
        {
            for(int i=0; i<pq.top().first; i++)
                ans += pq.top().second;
            pq.pop();
        }
        
        return ans;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(N)
