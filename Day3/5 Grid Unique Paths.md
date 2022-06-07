# [Grid Unique Paths](https://leetcode.com/problems/unique-paths/)

### Code || [Notes](https://drive.google.com/file/d/1AG2JoWhfgUsJX-FZvDt68HOuy9nXOL2Q/view?usp=sharing)

``` .cpp
class Solution {
public:
    int uniquePaths(int m, int n) {
        int N = m+n-2;
        int r = m-1;
        double ans=1;
        for(int i=1; i<=r; i++){
            ans = ans*(N-r+i)/i;
        }
        return (int)ans;
    }
};
```
