# [Tree Matching](https://cses.fi/problemset/task/1130)

## Code :
```python
dp[1..n][0..1] = 0

def dfs(u, p):
    for v in e[u]:
        if v==p :   continue
        dp[u][0] += max(dp[v][0], dp[v][1])
  
    for v in e[u]:
        if v==p :   continue
        dp[u][1] += max(dp[u][1], 1+dp[v][0]-dp[v][1]+dp[u][0])
    return

dfs(1, -1)
ans = max(dp[1][0], dp[1][1])
```
