# [Tree Diameter](https://cses.fi/problemset/task/1131) 

## Code
```python
dp[1..n]    
mx1from[1..n] = -1
mx1from[1..n] = -1

def dfs(u, p) : 
    mx1 = mx2 = -1
    for v in e[u] :
        if v == p : contunue
        cur = dfs(v, u)
        maintain_max_2((mx1, mx1from[u]), (mx2, mx2from[u]), (cur, v))
    dp[u] = 1 + max(mx1, 0) + max(mx2, 0)
    return 1 + max(mx1, 0)
    
 def construct(u) :
    path = []
    path.push_back(u);
    v1 = mx1from[u]
    while v1!=-1 :
        path.push_back(v1)
        v1 = mx1from[v1]
    v2 = mx2from[u]
    while v2!=-1 :
        path.push_back(v2)
        v2 = mx1from[v2]
        
 dfs(1, -1)
 
 ans = max(dp[1..n]) - 1 
 ```
