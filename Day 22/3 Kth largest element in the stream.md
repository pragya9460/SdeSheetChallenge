# [Kth largest element in the stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/)

### Code ||

``` .cpp
class KthLargest {
public:
    priority_queue<int, vector<int>, greater<int>> pq;
    int n;
    KthLargest(int k, vector<int>& nums) {
        this->n=k;
        for(int i=0; i<nums.size(); i++){
            pq.push(nums[i]);
            if(pq.size()>k){
                pq.pop();
            }
        }
    }
    
    int add(int val) {
        pq.push(val);
        if(pq.size()>n){
            pq.pop();
        }
        return pq.top();
    }
};
```

```
TC:- O(n log n)
SC:- O(k)
```
