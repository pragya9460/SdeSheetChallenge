# [Rotten oranges](https://leetcode.com/problems/rotting-oranges/)

### Code ||

``` .cpp
class Solution {
public:
    int orangesRotting(vector<vector<int>>& g) {
        if(g.empty())   return 0;
        int n =g.size(), m = g[0].size();
        int tcnt=0;
        queue<pair<int, int>> q;
        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                if(g[i][j]==2){
                    q.push({i, j});
                }
                if(g[i][j]!=0){
                    tcnt++;
                }
            }
        }
        int di[4] = {0, 0, 1, -1};
        int dj[4] = {1, -1, 0, 0};
        int mins=0, cnt=0;
        while(!q.empty()){
            int sze = q.size();
            cnt+= sze;
            for(int idx=0; idx<sze; idx++){
                int i = q.front().first;
                int j = q.front().second;
                q.pop();
                
                for(int ind=0; ind<4; ind++){
                    int ni = i + di[ind], nj = j + dj[ind];
                    if(ni<0 or nj<0 or ni>=n or nj>=m or g[ni][nj]!=1) continue;
                    g[ni][nj]=2;
                    q.push({ni, nj});
                }
            }
            if(!q.empty()){
                mins++;
            }
        }
        return tcnt==cnt?mins:-1;
    }
};
```

```
TC:- O(n*n*4)
SC:- O(n*n)
```
