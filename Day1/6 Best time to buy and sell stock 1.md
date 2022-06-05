# [Best time to buy and sell stock 1](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

### Code || [Notes](https://drive.google.com/file/d/11uQqPCThX8Mr6nt_80Z_ffY7bG2bm4K7/view?usp=sharing)

``` .cpp
class Solution {
public:
    int maxProfit(vector<int>& p) {
        int mini = p[0];
        int mx = INT_MIN;
        int n = p.size();
        for(int i=0; i<p.size(); i++){
            mx = max(mx, (p[i]-mini));
            mini = min(mini, p[i]);
        }
        return mx;
    }
};
```
