# [Combination Sum-I](https://leetcode.com/problems/combination-sum/)

### Code ||

``` .cpp
class Solution {
public:
    void f(int ind, int t, vector<vector<int>> &ans, vector<int> ds, vector<int> &c){
        if(ind==c.size()){
            if(t==0)    ans.push_back(ds);
            return;
        }
        if(c[ind]<=t){
            ds.push_back(c[ind]);
            f(ind, t-c[ind], ans, ds, c);
            ds.pop_back();
        }
        f(ind+1, t, ans, ds, c);
    }
    vector<vector<int>> combinationSum(vector<int>& c, int t) {
        vector<vector<int>> ans;
        vector<int> ds;
        f(0, t, ans, ds, c);
        return ans;
    }
};
```

```
TC:- O(2^t * k)
SC:- O(x * k) 
k is length of each combination 
x is number of combination
```
