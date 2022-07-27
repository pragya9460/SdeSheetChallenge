# [Strongly Connected Component(SCC, Kosaraju Algorithm)](https://practice.geeksforgeeks.org/problems/strongly-connected-components-kosarajus-algo/1)

### Code ||

``` .cpp
class Solution
{
	public:
	void dfs(int node, stack<int> &st, vector<int> &vis, vector<int> adj[]){
	    vis[node] = 1;
	    for(auto it: adj[node]){
	        if(!vis[it])    dfs(it, st, vis, adj);
	    }
	    st.push(node);
	}
	void revdfs(int node, vector<int> &vis, vector<int> transpose[]){
	    vis[node]=1;
	    for(auto it: transpose[node]){
	        if(!vis[it])    revdfs(it, vis, transpose);
	    }
	}
    int kosaraju(int v, vector<int> adj[]){
        stack<int> st;
        vector<int> vis(v, 0);
        for(int i=0; i<v; i++){
            if(!vis[i]){
                dfs(i, st, vis, adj);
            }
        }
        vector<int> transpose[v];
        for(int i=0; i<v; i++){
            vis[i]=0;
            for(auto it: adj[i]){
                transpose[it].push_back(i);
            }
        }
        int cnt=0;
        while(!st.empty()){
            int node = st.top();
            st.pop();
            if(!vis[node]){
                cnt++;
                revdfs(node, vis, transpose);
            }
        }
        return cnt;
    }
};
```

```
TC:- O(v+e)
SC:- O(n+e) + O(2n)
```
