---
title: "CodeForce: 445A"
categories: algorithm leetcode
---

445A. DZY Loves Chessboard (Python Version),

At first, I run build by dfs process. but it stack overflow..
So,, so simple version like for loop.
I think I should be careful to use recursive method...
- ver1) recursive method like DFS
- ver2) simple for loop method.

```python
# import sys
# sys.setrecursionlimit(5000)
m,n = map(int, input().split())
A = []
o = []
for ri in range(m):
    A += [[]]
    o += [[]]
    A[ri] += [i for i in input()]
    # A[ri] += [i for i in ".........................--..................-.............................--..................-...."]
    o[ri] += ["#" for i in range(n)]

"""
.........................--..................-....
"""
visited = [[False for i in range(n)] for j in range(m)]
def setChe(A, i, j, o, isW):
    global visited
    
    if i<0 or j<0 or i>=m or j>=n:
        return
    
    if A[i][j] == "-":
        o[i][j] = "-"
        return
    
    if visited[i][j]:
        return

    visited[i][j] = True
    
    if isW:
        value = "W"
    else:
        value = "B"
    
    o[i][j] = value
    
    setChe(A, i, j+1, o, not isW) 
    setChe(A, i+1, j, o, not isW)
    setChe(A, i-1, j, o, not isW)
    setChe(A, i, j-1, o, not isW)
    
    return 
    
for ri in range(m):
    for ci in range(n):
        if A[ri][ci] == ".":
            # set "W" or "B"
            if (ri+ci)%2:
                o[ri][ci] = "W"
            else:
                o[ri][ci] = "B"
            # setChe(A,ri,ci,o, False)
        elif A[ri][ci] == "-":
            o[ri][ci] = '-'


for ri in range(m):
    ts = ''
    for ci in range(n):
        ts += o[ri][ci]
    print(ts)

# print(o)        
```

refer to [this]

Algorithm category: DFS, brute force

[this]: https://codeforces.com/problemset/problem/445/A
