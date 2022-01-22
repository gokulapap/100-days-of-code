---
title: "Stone Game IV"
description: "There are n stones in a pile. Take stones in a optimal way to win"
categories:
  - math
  - DP
---

### Question

> Alice and Bob take turns playing a game, with Alice starting first.Initially, there are n stones in a pile. On each player's turn, that player makes a move consisting of removing any non-zero square number of stones in the pile. Also, if a player cannot make a move, he/she loses the game.

> Given a positive integer n, return true if and only if Alice wins the game otherwise return false, assuming both players play optimally.

```
Example 1:

Input: n = 1
Output: true
Explanation: Alice can remove 1 stone winning the game because Bob doesn't have any moves.

Example 2:

Input: n = 2
Output: false
Explanation: Alice can only remove 1 stone, after that Bob removes the last one winning the game (2 -> 1 -> 0).
```

### Code [C++]

```cpp
class Solution {
public:
    bool winnerSquareGame(int n) {
            if(n==0)
                return false;
            vector<bool> dp(n+1, false);        
            
            for(int i=1; i<=n; i++)
            {
                for(int j=1; j*j<=i; j++)
                {
                    if(dp[i-(j*j)]==false)
                    {
                        dp[i] = true;
                        break;
                    }
                }
            }

            return dp[n];
        }
};
```

> Time Complexity = O(N√N)

> Space Complexity = O(N)
