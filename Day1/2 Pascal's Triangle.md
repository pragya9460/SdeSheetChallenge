# [Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)

### Code || [Notes](https://drive.google.com/file/d/11nEPfaecbpHxK1bUjOE26TUVS2BHrhUa/view?usp=sharing)
``` .cpp
class Solution {
public:
    vector<vector<int>> generate(int n) {
        vector<vector<int>> dp;
        dp.push_back({1});
        if(n==1){
            return dp;
        }
        dp.push_back({1, 1});
        if(n==1){
            return dp;
        }
        vector<int> prev = {1, 1};
        for(int i=1; i<n-1; i++){
            vector<int> temp(i+2, 1);
            for(int j=1; j<=i; j++){
                temp[j]= prev[j] + prev[j-1];
            }
            dp.push_back(temp);
            prev = temp;
        }
        return dp;
    }
};
```

```
TC:- O(n²)
SC:- O(1)
```
