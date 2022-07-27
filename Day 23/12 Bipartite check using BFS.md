# [Bipartite check using BFS](https://leetcode.com/problems/is-graph-bipartite/)

### Code || 

``` .cpp
bool bipartite(vector<vector<int>>& g, vector<int>& col, int node){
        queue<int> q;
        col[node] = 1;
        q.push(node);
        while(!q.empty()){
            int cur = q.front();
            q.pop();
            for(auto it: g[cur]){
                if(col[it]==-1){
                    col[it] = 1-col[cur];
                    q.push(it);
                }
                else if(col[it]==col[cur]){
                    return false;
                }
            }
        }
        return true;
    }
    bool isBipartite(vector<vector<int>>& g) {
        int n = g.size();
        vector<int> color(n, -1);
        for(int i=0; i<n; i++){
            if(color[i]==-1){
                if(!bipartite(g, color, i)){
                    return false;
                }
            }
        }
        return true;
    }
```

```
TC:- O(n+e)
SC:- O(n) + O(n)
```
