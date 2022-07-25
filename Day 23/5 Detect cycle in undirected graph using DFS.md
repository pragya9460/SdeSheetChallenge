# [Detect cycle in undirected graph using DFS](https://practice.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1)

### Code ||

``` .cpp
    bool cycle(int i, vector<int> adj[], vector<int> &vis, int par){
        vis[i] = 1;
        for(auto it: adj[i]){
            if(!vis[it]){
                if(cycle(it, adj, vis, i))  return true;
            }
            else if(it!=par){
                return true;
            }
        }
        return false;
    }
    bool isCycle(int v, vector<int> adj[]) {
        vector<int> vis(v, 0);
        for(int i=0; i<v; i++){
            if(!vis[i]){
                if(cycle(i, adj, vis, -1))  return true;
            }
        }
        return false;
    }
```

```
TC:- O(v+e)
SC:- O(v+e) + O(n)
```
