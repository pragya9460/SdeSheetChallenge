# [Trapping the rain water](https://leetcode.com/problems/trapping-rain-water/)

### Code ||

``` .cpp
class Solution {
public:
    int trap(vector<int>& h) {
        int n = h.size();
        int l = 0, r = n-1;
        int lmax = 0, rmax=0, res=0;
        while(l<=r){
            if(h[l]<=h[r]){
                if(h[l]>=lmax)  lmax = h[l];
                else    res+= lmax-h[l];
                l++;
            }
            else{
                if(h[r]>=rmax)  rmax = h[r];
                else    res+= rmax-h[r];
                r--;
            }
        }
        return res;
    }
};
```
