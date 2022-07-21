# [Flatten BT to LL](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

### Code||

``` .cpp
class Solution {
public:
    void f(TreeNode* root){
        if(root==NULL or (root->left==NULL and root->right==NULL)){
            return;
        }
        if(root->left){
            f(root->left);
            TreeNode* temp = root->right;
            root->right = root->left;
            root->left = NULL;
            TreeNode* cur = root->right;
            while(cur->right){
                cur= cur->right;
            }
            cur->right = temp;
        }
        f(root->right);
    }
    void flatten(TreeNode* root) {
        if(root==NULL){
            return;
        }
        return f(root);
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
