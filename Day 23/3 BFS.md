# [BFS](https://practice.geeksforgeeks.org/problems/bfs-traversal-of-graph/1)

### Code ||

``` .cpp
    vector<int> bfsOfGraph(int v, vector<int> adj[]) {
        if(v==1)    return {0};
        vector<int> bfs;
        vector<int> vis(v, 0);
        queue<int> q;
        q.push(0);
        while(!q.empty()){
            int node = q.front();
            q.pop();
            bfs.push_back(node);
            for(auto it: adj[node]){
                if(!vis[it]){
                    q.push(it);
                    vis[it]=1;
                }
            }
        }
        return bfs;
    }
```

```
TC:- O(v+e)
SC:- O(v+e) + O(n)
```
