# [Detect a cycle in directed graph using BFS(Kahn's Algorithm)](https://leetcode.com/problems/course-schedule/)

### Code ||

``` .cpp
class Solution {
public:
    bool cycle(int i, vector<int> adj[], vector<int> &vis){
        queue<pair<int, int>> q;
        q.push({i, -1});
        vis[i] = 1;
        while(!q.empty()){
            int node = q.front().first;
            int par = q.front().second;
            q.pop();
            for(auto it: adj[node]){
                if(!vis[it]){
                    q.push({it, node});
                    vis[it]= 1;
                }
                else if(it!=par){
                    return true;
                }
            }
        }
        return false;
    }
    bool canFinish(int n, vector<vector<int>>& p) {
        if(p.size()==0) return true;
        vector<int> vis(n, 0);
        vector<int> adj[n];
        for(int i=0; i<p.size(); i++){
            adj[p[i][1]].push_back(p[i][0]);
        }
        for(int i=0; i<n; i++){
            if(!vis[i]){
                if(cycle(i, adj, vis))    return false;
            }
        }
        return true;
    }
};
```

```
TC:- O(n+e)
SC:- O(n) + O(n)
```
