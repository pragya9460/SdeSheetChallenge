# [Rotate Image](https://leetcode.com/problems/rotate-image/)

### Code || [Notes](https://drive.google.com/file/d/1AW8LEj23xRz8Q7hDA50ysxl3kh7MjYy4/view?usp=sharing)

``` .cpp
class Solution {
public:
    void rotate(vector<vector<int>>& mat) {
        int n=mat.size();
        //transpose of matrix
        for(int i=0; i<n; i++){
            for(int j=0; j<i; j++){
                swap(mat[i][j], mat[j][i]);
            }
        }
        for(int i=0; i<n; i++){
            reverse(mat[i].begin(), mat[i].end());
        }
        return;
    }
};
```

```
TC:- O(n²)
SC:- O(1)
```
