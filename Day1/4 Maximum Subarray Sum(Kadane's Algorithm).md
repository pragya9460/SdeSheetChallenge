# [Maximum Subarray Sum(Kadane's Algorithm)](https://leetcode.com/problems/maximum-subarray/)

### Code || [Notes](https://drive.google.com/file/d/11kaoR_ZNORTFYpgQKfgHO1EaDIPvjZ6u/view?usp=sharing)

``` .cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int mx=INT_MIN;
        int sum=0;
        for(auto it: nums){
            sum+=it;
            mx = max(mx, sum);
            if(sum<0) sum=0;
        }
        return mx;
    }
};
```

```
TC:- O(n)
SC:- O(1)
```
