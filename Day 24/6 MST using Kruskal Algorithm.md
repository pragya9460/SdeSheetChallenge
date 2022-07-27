# [MST using kruskal Algorithm](https://www.codingninjas.com/codestudio/problems/1082553?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website&leftPanelTab=1)

### Code ||

``` .cpp
#include <bits/stdc++.h>
using namespace std;

bool comp(vector<int>&a,vector<int>&b){
    return a[2]<b[2];
}
int findpar(int u,vector<int>&par){ 
    if(u==par[u]) 
        return u; 
    return par[u]= findpar(par[u],par); 
}

int union_(int u, int v, vector<int> &par){
    if(findpar(u,par)==findpar(v,par))  
        return 0;
    else if(!(u>=0 && v>=0 && u<par.size() && v<par.size())) 
        return 0; 
    par[u]=v; 
}

int kruskalMST(int n, int m, vector<vector<int>> &edges) {
    sort(edges.begin(),edges.end(),comp);
    vector<int> parent(n+1);
    for(int i=0;i<parent.size();i++) 
        parent[i]=i;
    
    int cost=0;
    for(auto it:edges){
        if(findpar(it[0],parent)!=findpar(it[1],parent)){ 
            cost+=it[2]; 
            union_(findpar(it[0],parent),findpar(it[1],parent),parent); 
        }
    }
    return cost;
}

```

```
TC:- O(e log e)
SC:- O(2n)
```
