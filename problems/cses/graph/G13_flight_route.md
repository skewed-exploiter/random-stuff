# [Flight Routes](https://cses.fi/problemset/task/1196/)
We will maintain max_priority_queue for each vertex of having maximum size `k`.

For each vertex `v`, `best[v]` will contain best minimum distances

>when `d > best[u].top()`  we must have already processed all elements in `best[u]` so no need to proceed further
>
>his was the main understanding required in the problem
>
>In this problem other things are very clear but till  when we will need to visit the vertex is not clear.


otherwise we will maintain `k` minimum distances in `best[v]` for vertices in `e[u]`

___Complexity___ : _O(mk log mk)_

## Code
```python
max_priority_queue best[1..n]
min_priority_queue q

q.push((0,1))
best[1].push(0)
while q not empty :
    (d, u) = q.pop()
    if d > best[u].top() :
        continue
    for edge in e[u] :
        (v, w) = edge
        if best[v].size() < k :
            best[v].push(d+w)
            q.push((d+w, v))
        else if d+w < best[v].top() :
            best[v].pop()
            best[v].push(d+w)
            q.push((d+w, v))
              
ans = reverse(best[n])
```
