# [Search in a 2D matrix](https://leetcode.com/problems/search-a-2d-matrix/)

### Code || [Notes](https://drive.google.com/file/d/1Nuaf5sEfixrEe_bMtQg5GHt6nPOp-MG4/view?usp=sharing)
``` .cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& mat, int t) {
        int r = mat.size(), c=mat[0].size();
        int m=0, n=c-1;
        while(m<r and n>=0){
            int mid = mat[m][n];
            if(mid==t){
                return true;
            }
            else if(mid>t){
                n--;
            }
            else if(mid<t){
                m++;
            }
        }
        return false;
    }
};
```

```
TC:- O(m+n)
SC:- O(1)
```
