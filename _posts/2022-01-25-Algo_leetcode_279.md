---
title: "LeetCode: 279.Perfect squre"
categories: algorithm leetcode
---
How to find out the least number of squre
let's get started!

```python
class Solution:
    def numSquares(self, n: int) -> int:
        queue = [[n, 1]]
        visited = [False for i in range(10001)]

        while queue:
            v, depth = queue.pop(0)
            for i in range(1,101):
                temp = v - i**2
                if visited[temp]:
                    continue
                if temp == 0:
                    return depth
                elif temp > 0:
                    visited[temp] = True
                    queue.append( [temp, depth+1] )
                else:
                    break
```
refer to [this]

Algorithm category: BFS

[this]: https://leetcode.com/problems/perfect-squares/
