# [Top k frequent elements](https://leetcode.com/problems/top-k-frequent-elements/)

### Code ||

``` .cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& arr, int k) {
        int n = arr.size();
        unordered_map<int, int> m;
        for(int i=0; i<n; i++){
            m[arr[i]]++;
        }
        vector<int> freq[n + 1];
        for (int i = 0; i < n; i++) {
            int f = m[arr[i]];
            if (f != -1) {
                freq[f].push_back(arr[i]);
                m[arr[i]] = -1;
            }
        }
        int count = 0;
        vector<int> ans;
        for (int i = n; i >= 0; i--) {
            for (int x : freq[i]) {
                ans.push_back(x);
                count++;
                if (count == k)
                    return ans;
            }
        }
        return ans;
    }
};
```
```
TC:- O(n)
SC:- O(n)
```
