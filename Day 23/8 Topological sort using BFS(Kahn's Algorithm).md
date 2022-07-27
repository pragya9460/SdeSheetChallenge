# [Topological sort using BFS(Kahn's Algorithm)](https://practice.geeksforgeeks.org/problems/topological-sort/1)

### Code ||

``` .cpp
vector<int> topoSort(int v, vector<int> adj[]) 
	{
	     queue<int> q;
	     vector<int> in(v, 0);
	     for(int i=0; i<v; i++){
	         for(auto it: adj[i]){
	             in[it]++;
	         }
	     }
	     for(int i=0; i<v; i++){
	         if(in[i]==0)   q.push(i);
	     }
	     vector<int> topo;
	     while(!q.empty()){
	         int node = q.front();
	         q.pop();
	         topo.push_back(node);
	         for(auto it: adj[node]){
	             in[it]--;
	             if(in[it]==0){
	                 q.push(it);
	             }
	         }
	     }
	     return topo;
	}
```

```
TC:- O(n+e)
SC:- O(n) + O(n)
```
