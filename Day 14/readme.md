---
title: "Sieve of Eratosthenes"
description: "Find all the Prime numbers in the given range"
categories:
  - Math
  - Sieve
---

### Question

> Given a number N, calculate all the prime numbers up to N using Sieve of Eratosthenes.

```
Input:
N = 10

Output:
2 3 5 7

Explanation:
Prime numbers less than equal to N 
are 2 3 5 and 7
```

### Code [C++]

```cpp
class Solution
{
public:
    vector<int> sieveOfEratosthenes(int N)
    {
        vector<int> primes;
        vector<bool> nums(N+1, true);
        int n = 2;
        for(int i=n; n*n <= N; n++)
        {
            for(int j=n*n; j<=N; j+=n)
            {
                nums[j] = false;
            }
        }
        for(int i=2; i<=N; i++)
        {
            if(nums[i])
                primes.push_back(i);
        }
        return primes;
    }
};
```
> Time Complexity = O(N)

> Space Complexity = O(N)
