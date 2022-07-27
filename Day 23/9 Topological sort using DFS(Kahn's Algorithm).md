# [Topological sort using DFS](https://practice.geeksforgeeks.org/problems/topological-sort/1)

### Code ||

``` .cpp
void dfs(int i, vector<int> &vis, vector<int> &topo, vector<int> adj[]){
	    vis[i]=1;
	    for(auto it: adj[i]){
	        if(!vis[it])
	            dfs(it, vis, topo, adj);
	    }
	    topo.push_back(i);
	}
	vector<int> topoSort(int v, vector<int> adj[]) 
	{
	     vector<int> vis(v, 0);
	     vector<int> topo;
	     for(int i=0; i<v; i++){
	         if(!vis[i])
	            dfs(i, vis, topo, adj);
	     }
	     reverse(topo.begin(), topo.end());
	     return topo;
	}
```

```
TC:- O(v+e)
SC:- O(v+e) + O(n)
```
