# [Diameter of BT](https://leetcode.com/problems/diameter-of-binary-tree/)

### Code ||

``` .cpp
class Solution {
public:
    int f(TreeNode* root, int &d){
        if(root==NULL){
            return 0;
        }
        int lh =f(root->left, d);
        int rh =f(root->right, d);
        d = max(d, lh+rh);
        return 1 + max(lh, rh);
    }
    int diameterOfBinaryTree(TreeNode* root) {
        if(root==NULL)  return 0;
        int d = 0;
        f(root, d);
        return d;
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
