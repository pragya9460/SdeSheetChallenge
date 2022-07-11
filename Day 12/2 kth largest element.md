# [Kth largest element](https://leetcode.com/problems/kth-largest-element-in-an-array/)


### Code ||
``` .cpp
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        priority_queue <int, vector <int>, greater <int>> pq;
        for(int i=0; i<nums.size(); i++){
            pq.push(nums[i]);
            if(pq.size()>k){
                pq.pop();
            }
        }
        return pq.top();
    }
};
```

```
TC:- O(nlog n)
SC:- O(1)
```
