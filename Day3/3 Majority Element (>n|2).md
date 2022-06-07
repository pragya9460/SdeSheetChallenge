# [Majority Element (>n/2)](https://leetcode.com/problems/majority-element/)

### Code || [Notes](https://drive.google.com/file/d/1IkJ1S2YCPqFOGko7hlwTUvEMFV8rsTNP/view?usp=sharing)

``` .cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int cnt=0, cnd=0;
        for(auto it: nums){
            if(cnt==0){
                cnd=it;
            }
            if(it==cnd){
                cnt++;
            }
            else{
                cnt--;
            }
        }
        return cnd;
    }
};
```
