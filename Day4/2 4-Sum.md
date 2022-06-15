# [4 Sum](https://leetcode.com/problems/4sum/)

### Code || [Notes](https://drive.google.com/file/d/1705DA3TWyT4oXqb1a5UjBVRCepHGy_sr/view?usp=sharing)
``` .cpp
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int t1) {
        vector<vector<int>> res;
        if(nums.size()<4){
            return res;
        }
        int n=nums.size();
        sort(nums.begin(), nums.end());
        for(int i=0; i<n; i++){
            for(int j=i+1; j<n; j++){
                int t2 = t1-nums[j]-nums[i];
                
                int front = j+1;
                int back = n-1;
                while(front<back){
                    int ts = nums[front] + nums[back];
                    if(ts<t2) front++;
                    else if(ts>t2) back--;
                    else{
                        vector<int > quad(4, 0);
                        quad[0] = nums[i];
                        quad[1] = nums[j];
                        quad[2] = nums[front];
                        quad[3] = nums[back];
                        res.push_back(quad);
                        
                        
                        while(front<back and nums[front]==quad[2]) ++front;
                        while(front<back and nums[back]==quad[3]) --back;
                    }
                }
                
                while(j+1<n and nums[j+1]==nums[j]) ++j;
            }
            while(i+1<n and nums[i+1]==nums[i]) ++i;
        }
        return res;
    }
};
```

```
TC:- O(n³)
SC:- O(1)
```
