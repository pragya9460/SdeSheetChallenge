# [Number of islands using BFS](https://leetcode.com/problems/number-of-islands/)

### Code ||

``` .cpp
class Solution {
public:
    void f(vector<vector<char>> &g, int i, int j){
        queue<pair<int, int>> q;
        q.push({i, j});
        while(!q.empty()){
            int r = q.front().first;
            int c = q.front().second;
            q.pop();
            int dx[4] = {1, -1, 0, 0};
            int dy[4] = {0, 0, -1, 1};
            for(int ind=0; ind<4; ind++){
                int nr = r + dx[ind];
                int nc = c + dy[ind];
                if(nr>=g.size() or nr<0 or nc>=g[0].size() or nc<0 or g[nr][nc]=='0' or g[nr][nc]=='2')
                    continue;
                q.push({nr, nc});
                g[nr][nc] = '2';
            }
        }
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
SC:- O(n)
```
