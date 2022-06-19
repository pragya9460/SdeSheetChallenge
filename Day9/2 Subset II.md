# [Subset II](https://leetcode.com/problems/subsets-ii/)

### Code ||

``` .cpp
class Solution {
public:
    void sub(int ind, vector<int> &nums, vector<int> &ds, vector<vector<int>> &ans){
        ans.push_back(ds);
        for(int i=ind; i<nums.size(); i++){
            if(i!=ind and nums[i]==nums[i-1])   continue;
            ds.push_back(nums[i]);
            sub(i+1, nums, ds, ans);
            ds.pop_back();
        }
    }
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<vector<int>> ans;
        vector<int> ds;
        sort(nums.begin(), nums.end());
        sub(0, nums, ds, ans);
        return ans;
    }
};
```

```
TC:- O(2^n)
SC:- O(2^n * k) + O(n)  ---> k is size of each subset and extra O(n) is auxialliary stack space.
```
