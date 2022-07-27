# [Dijkastra Algorithm(Shortest path in undirected weighted graph)](https://practice.geeksforgeeks.org/problems/implementing-dijkstra-set-1-adjacency-matrix/1)

### Code ||

``` .cpp
    vector <int> dijkstra(int v, vector<vector<int>> adj[], int s)
    {
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
        vector<int> d(v, INT_MAX);
        d[s]=0;
        pq.push({0, s});
        while(!pq.empty()){
            int dist = pq.top().first;
            int node = pq.top().second;
            pq.pop();
            for(auto it: adj[node]){
                int nd = it[1];
                int nn = it[0];
                if(d[nn]>dist+nd){
                    d[nn] = dist+nd;
                    pq.push({d[nn], nn});
                }
            }
        }
        return d;
    }
```

```
TC:- O(v+e)
SC:- O(v)
```
