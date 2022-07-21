# [Maximum Path Sum]()

### Code ||

``` .cpp
class Solution {
public:
    int f(TreeNode* root, int &mx){
        if(root==NULL){
            return 0;
        }
        int lmx = max(0, f(root->left, mx));
        int rmx = max(0, f(root->right,  mx));
        mx = max(mx, lmx + rmx + root->val);
        return max(lmx, rmx) + root->val;
    }
    int maxPathSum(TreeNode* root) {
        if(root==NULL)  return 0;
        int mx = INT_MIN;
        f(root, mx);
        return mx;
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
