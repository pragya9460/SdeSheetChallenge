# [Number of Island using DFS](https://leetcode.com/problems/number-of-islands/)

### Code ||

``` .cpp
class Solution {
public:
    void f(vector<vector<char>> &g, int i, int j){
        if(i>=g.size() or i<0 or j>=g[0].size() or j<0 or g[i][j]=='0' or g[i][j]=='2')
            return;
        
        g[i][j]='2';
        f(g, i, j-1);
        f(g, i, j+1);
        f(g, i-1, j);
        f(g, i+1, j);
        
        return;
    }
    int numIslands(vector<vector<char>>& g) {
        int m = g.size(), n = g[0].size();
        int num =0;
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(g[i][j]=='1'){
                    num++;
                    f(g, i, j);
                }
            }
        }
        return num;
    }
};
```

```
TC:- O(n+e)
SC:- O(n+e)
```
