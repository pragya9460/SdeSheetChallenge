# [Detect Cycle in Direct graph using DFS](https://practice.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1)

### Code ||

``` .cpp
    bool cycle(vector<int> &vis, vector<int> &dfsvis, vector<int> adj[], int i){
        vis[i]=1;
        dfsvis[i]=1;
        for(auto it: adj[i]){
            if(!vis[it]){
                if(cycle(vis, dfsvis, adj, it)){
                    return true;
                }
            }
            else if(dfsvis[it]){
                return true;
            }
        }
        dfsvis[i]=0;
        return false;
    }
    
    bool isCyclic(int v, vector<int> adj[]) {
        vector<int> vis(v, 0);
        vector<int> dfsvis(v, 0);
        for(int i=0; i<v; i++){
            if(!vis[i]){
                if(cycle(vis, dfsvis, adj, i)){
                    return true;
                }
            }
        }
        return false;
    }
```

```
TC:- O(v+e)
SC:- O(v+e) + O(n) + O(n)
```
