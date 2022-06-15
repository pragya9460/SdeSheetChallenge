# [Max consecutive ones](https://leetcode.com/problems/max-consecutive-ones/)

### Code ||

``` .cpp
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int curr=0;
        int mx = 0;
        for(int i=0; i<nums.size(); i++){
            if(nums[i]==1){
                curr++;
            }
            else{
                curr = 0;
            }
            mx = max(mx, curr);
        }
        return mx;
    }
};
```
