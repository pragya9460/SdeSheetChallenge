# [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)

### Code || [Notes](https://drive.google.com/file/d/1Ore77bHU5SdMzpJGm7hID7OwMsv53N9i/view?usp=sharing)
``` .cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_set<int> s;
        for(int i=0; i<nums.size(); i++){
            s.insert(nums[i]);
        }
        int mx_len=0;
        for(int i=0; i<nums.size(); i++){
            if(s.find(nums[i]-1)==s.end()){
                int j=1;
                while(s.find(nums[i]+j)!=s.end()){
                    j++;
                }
                mx_len = max(mx_len, j);
            }
        }
        return mx_len;
    }
};
```
