# [Check if BT is BST or not](https://leetcode.com/problems/validate-binary-search-tree/)

### Code ||

``` .cpp
class Solution {
public:
    bool f(TreeNode* root, long long lb, long long ub){
        if(root==NULL){
            return true;
        }
        if(root->val>=ub or root->val<=lb){
            return false;
        }
        return f(root->left, lb, root->val) and f(root->right, root->val, ub);
    }
    bool isValidBST(TreeNode* root) {
        if(root==NULL or (root->left==NULL and root->right==NULL)){
            return true;
        }
        return f(root, LONG_MIN, LONG_MAX);
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
