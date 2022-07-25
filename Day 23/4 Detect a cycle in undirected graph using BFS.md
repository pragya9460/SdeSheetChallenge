# [Detect cycle in undirected graph using BFS](https://practice.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1)

### Code ||

``` .cpp
class Solution{
  public:
  bool bfs(int i, vector<int> adj[], vector<bool> &vis){
        queue<pair<int, int>> q;
        q.push({i, -1});
        vis[i] = true;
        while(!q.empty()){
            int node = q.front().first;
            int par = q.front().second;
            q.pop();
            for(auto it: adj[node]){
                if(!vis[it]){
                    q.push({it, node});
                    vis[it]= true;
                }
                else if(it!=par){
                    return true;
                }
            }
        }
        return false;
    }
    
    bool isCycle(int v, vector<int> adj[]) {
        vector<bool> vis(v, false);
        for(int i=0; i<v; i++){
            if(!vis[i]){
                if(bfs(i, adj, vis))    return true;
            }
        }
        return false;
    }
}
```

```
TC:- O(v+e)
SC:- O(v+e) + O(n)
```
