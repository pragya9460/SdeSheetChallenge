# [Combination Sum-II](https://leetcode.com/problems/combination-sum-ii/)

### Code ||

``` .cpp
class Solution {
public:
    void f(int ind, int t, vector<vector<int>> &ans, vector<int> ds, vector<int> &c){
        if(t==0){
            ans.push_back(ds);
            return;
        }
        for(int i=ind; i<c.size(); i++){
            if(i>ind and c[i]==c[i-1])  continue;
            if(c[i]>t) break;
            ds.push_back(c[i]);
            f(i+1, t-c[i], ans, ds, c);
            ds.pop_back();
        }
    }
    vector<vector<int>> combinationSum2(vector<int>& c, int t) {
        sort(c.begin(), c.end());
        vector<vector<int>> ans;
        vector<int> ds;
        f(0, t, ans, ds, c);
        return ans;
    }
}; 
```

```
TC:- O(2^n * k)
SC:- O(x*k)

where x is number of combinations, 
k is max size of combinations.
```
