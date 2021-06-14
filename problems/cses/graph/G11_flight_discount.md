# [Flight Discount](https://cses.fi/problemset/task/1195)
This is a slight modification on _Dijkstra's Algorithm_.

Let's create a new graph with `2n` nodes with `(u, used)` and edges.
1. `((u, 0), (v,0), w)`
2. `((u, 0), (v,1), w/2)`
3. `((u, 1), (v,1), w)`

clearly applying _Dijkstra's Algorithm_ on this graph will give shortest path from node `(1, 0)` to `(n, 1)`

## Code
```python
min_priority_queue q
d[1..n][0..1] = INF
vis[1..n][0..1] = False

def consider_edge((u, used1), (v, used2), w):
    if d[v][used2] > d[u][used1] + w :
        d[v][used2] = d[u][used1] + w
        q.push((w,(v, used2))

q.push((w, (1, 0)))
d[1][0] = 0

while not q.empty() :
    (u, used) = q.pop()
    if vis[u][used] :
        continue
    vis[u][used]=True
    for edge in e[u]:
        (v, w) = edge
        if used :
              consider_edge((u, 1), (v, 1), w)
        else :
              consider_edge((u, 0), (v, 0), w)
              consider_edge((u, 0), (v, 1), w/2)

ans = d[n][1]
```
