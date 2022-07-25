# [DFS](https://practice.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1)

### Code ||

``` .cpp
    void dfs(int v, vector<int> adj[], vector<int> &vis, vector<int> &ans, int node){
        vis[node] = 1;
        ans.push_back(node);
        for(auto it: adj[node]){
            if(!vis[it]){
                dfs(v, adj, vis, ans, it);
            }
        }
    }
    
    vector<int> dfsOfGraph(int v, vector<int> adj[]) {
        if(v==1)    return {0};
        vector<int> ans;
        vector<int> vis(v, 0);
        for(int i=0; i<v; i++){
            if(!vis[i]){
                dfs(v, adj, vis, ans, i);
            }
        }
        return ans;
    }
```

```
TC:- O(V+E)
SC:- O(V)
```
