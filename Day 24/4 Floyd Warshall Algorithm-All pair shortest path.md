# [Floyd Warshall Algorithm](https://practice.geeksforgeeks.org/problems/implementing-floyd-warshall2042/1)

### Code ||

``` .cpp
  void shortest_distance(vector<vector<int>>&d){
      // All pair shortest path
	    int n = d.size();
	    for(int k=0; k<n; k++){
	        for(int i=0; i<n; i++){
	            for(int j=0; j<n; j++){
	                if(d[i][k]!=-1 and d[k][j]!=-1 and d[i][j]==-1){
	                    d[i][j] = d[i][k] + d[k][j];
	                }
	                else if(d[i][j]>(d[i][k] + d[k][j]) and (d[i][k]!=-1 and d[k][j]!=-1)){
	                    d[i][j] = d[i][k] + d[k][j];
	                } 
	            }
	        }
	    }
	}
  
```

```
TC:- O(n^3)
SC:- O(1)
```
