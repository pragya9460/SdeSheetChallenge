# [Flood fill](https://leetcode.com/problems/flood-fill/)

### Code ||

``` .cpp
class Solution {
public:
    void f(vector<vector<int>>& im, int sr, int sc, int color, int src){
        if(sr>=im.size() or sc>=im[0].size() or sr<0 or sc<0)   return;
        else if(im[sr][sc]!=src)   return;
        im[sr][sc] = color;
        f(im, sr, sc-1, color, src);
        f(im, sr, sc+1, color, src);
        f(im, sr-1, sc, color, src);
        f(im, sr+1, sc, color, src);
    }
    vector<vector<int>> floodFill(vector<vector<int>>& im, int sr, int sc, int color) {
        if(im[sr][sc]==color)   return im;
        int src = im[sr][sc];
        f(im,sr, sc, color, src);
        return im;
    }
};
```

```
TC:- O(m*n)
SC:- O(m*n), --> recursion stack space
```
