# [Bellman Ford Algorithm to detect negative weight cycle in graph](https://practice.geeksforgeeks.org/problems/distance-from-the-source-bellman-ford-algorithm/0?fbclid=IwAR2_lL0T84DnciLyzMTQuVTMBOi82nTWNLuXjUgahnrtBgkphKiYk6xcyJU)

### Code ||

``` .cpp
    vector <int> bellman_ford(int v, vector<vector<int>> adj, int s) {
        vector<int> d(v, 1e8);
        d[s] = 0;
        for(int i=0; i<v; i++){
            for(auto it: adj){
                int u = it[0], v = it[1], w = it[2];
                if(d[u]!=INT_MAX and d[v]>d[u]+w){
                    d[v] = d[u] + w;
                }
            }
        }
        return d;
    }
```

```
TC:- O(v+e)
SC:- O(1)
```
