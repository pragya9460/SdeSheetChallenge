# [Bipartite check using DFS](https://practice.geeksforgeeks.org/problems/bipartite-graph/1)

### Code ||

``` .cpp
 bool bipartite(vector<int>adj[], int i, vector<int> &col){
        if(col[i]==-1)  col[i]=1;
        for(auto it: adj[i]){
            if(col[it]==-1){
                col[it] = 1-col[i];
                if(!bipartite(adj, it, col))    return false;
            }
            else if(col[it]==col[i]){
                return false;
            }
        }
        return true;
    }
	bool isBipartite(int v, vector<int>adj[]){
	    vector<int> col(v, -1);
	    
	    for(int i=0; i<v; i++){
	        if(col[i]==-1){
	            if(!bipartite(adj, i, col)) return false;
	        }
	    }
	    return true;
	}
```

```
TC:- O(v+e)
SC:- O(v+e) + O(v)
```
