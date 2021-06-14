# [Investigation](https://cses.fi/problemset/task/1202)

This problems asks for number minimum weight paths, minimum and maximum edges in minimum length paths which can be solved through simple exension to _Dijkstra's Algorithm_ 

>In this problem we need to stop overcounting by checking `u != prevu` in each iteration 

## Code
```python
min_priority_queue q
d[1..n] = INF
mn[1..n] = INF
mx[1..n] = -INF
routes[1..n] = 0

d[1] = mn[1] = mx[1] = 0
routes[1] = 1
q.push((0, 1))
prevu = u

while q not empty :
    (l, u) = q.pop()
    if u==prevu or d[u]<l :
        continue
    for edge in e[u] :
        (v, w) = edge
        if l+w < d[v] :
            d[v] = l+w
            mn[v] = mn[u]+1
            mx[v] = mx[u]+1
            routes[v] = routes[u]
            q.push((d[v], v))
        else if l+w == d[v] :
            mn[v] = min(mn[v], mn[u]+1)
            mx[v] = max(mx[v], mx[u]+1)
            routes[v] += routes[u]
            q.push((d[v], v))
            
 ans = d[n], routes[n], mn[n], mx[n]
```
