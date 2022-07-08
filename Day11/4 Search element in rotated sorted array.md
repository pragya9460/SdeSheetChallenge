# [Search element in rotated sorted array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

### Code ||

``` .cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int beg=0,end=nums.size()-1,mid;
        while(beg<=end)
        {
            mid=(beg+end)>>1;
            if(nums[mid]==target)
                return mid;
            if(nums[beg]<=nums[mid])
            {
                if(target<=nums[mid] && target>=nums[beg])
                    end=mid-1;
                else
                    beg=mid+1;
            }
            
            else
            {
                if(target>=nums[mid] && target<=nums[end])
                   beg=mid+1;
                else
                    end=mid-1;
            }
            
        }
        return -1;
    }
};
```

```
TC:- O(log n)
SC:- O(1)
```
