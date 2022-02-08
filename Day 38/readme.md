---
title: "Sum of Digits of String After Convert"
description: "Return the resulting integer after performing the operations"
categories:
  - string
  - sum
---

### Question

> You are given a string s consisting of lowercase English letters, and an integer k.
> First, convert s into an integer by replacing each letter with its position in the alphabet (i.e., replace 'a' with 1, 'b' with 2, ..., 'z' with 26). Then, transform the integer by replacing it with the sum of its digits. Repeat the transform operation k times in total.

> For example, if s = "zbax" and k = 2, then the resulting integer would be 8 by the following operations:
```
Convert: "zbax" ➝ "(26)(2)(1)(24)" ➝ "262124" ➝ 262124
Transform #1: 262124 ➝ 2 + 6 + 2 + 1 + 2 + 4 ➝ 17
Transform #2: 17 ➝ 1 + 7 ➝ 8
```
> Return the resulting integer after performing the operations described above.

```
Input: s = "iiii", k = 1
Output: 36
Explanation: The operations are as follows:
- Convert: "iiii" ➝ "(9)(9)(9)(9)" ➝ "9999" ➝ 9999
- Transform #1: 9999 ➝ 9 + 9 + 9 + 9 ➝ 36
Thus the resulting integer is 36.
```

### Code [C++]

```cpp
class Solution {
public:
    int sumDigits(int num) {
        int sum = 0;
        while(num > 0) 
        { 
            sum += num%10;
            num /= 10;
        }
        return sum;
    }
    
    int getLucky(string s, int k) {
        int sum = 0;
        for(char &ch : s) {
		    int val = ch-'a'+1;
		    sum += val < 10 ? val : (val%10 + val/10);
		}

        k -= 1;
        while(k-- && sum >= 10) 
            sum = sumDigits(sum);
        
        return sum;
    }
};
```

> Time Complexity = O(N)

> Space Complexity = O(1)
