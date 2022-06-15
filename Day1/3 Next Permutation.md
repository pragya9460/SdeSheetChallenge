# [Next Permutation](https://leetcode.com/problems/next-permutation/)

### Code || [Note](https://drive.google.com/file/d/11lZlF6Plh-yoMTHDeOMSwszoZiyAZ2ss/view?usp=sharing)

``` .cpp
class Solution{
public:
    void nextPermutation(vector<int>& nums) {
        int n=nums.size(), l, k;
        for(k=n-2; k>=0; k--){
            if(nums[k]<nums[k+1]){
                break;
            }
        }
        if(k<0){
            reverse(nums.begin(), nums.end());
        }
        else{
            for(l=n-1; l>k; l--){
                if(nums[l]>nums[k]){
                    break;
                }
            }
            swap(nums[k], nums[l]);
            reverse(nums.begin()+k+1, nums.end());
        }
    }
};
```

```
TC:- O(n)
SC:- O(1)
```
