# [Symmetric BT](https://leetcode.com/problems/symmetric-tree/)

### Code ||

``` .cpp
class Solution {
public:
    bool f(TreeNode* l, TreeNode* r){
        if(l==NULL or r==NULL){
            return l==r;
        }
        if(l->val!=r->val){
            return false;
        }
        return f(l->left, r->right) and f(l->right, r->left);
    }
    bool isSymmetric(TreeNode* root) {
        if(root->left==NULL and root->right==NULL){
            return true;
        }
        return f(root->left, root->right);
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
