# [2 Sum](https://leetcode.com/problems/two-sum/)

### Code || [Notes](https://drive.google.com/file/d/1PNR4mzeDDWsattRLKCCLMnn5MKRFVIPF/view?usp=sharing)
``` .cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
		unordered_map<int, int> m;
        vector<int> ans;
        for(int i=0; i<nums.size(); i++){
            if(m.find(target-nums[i])!=m.end()){
                ans.push_back(m[target-nums[i]]);
                ans.push_back(i);
            }
            else{
                m[nums[i]]=i;
            }
        }
        return ans;
    }
}; 
```
