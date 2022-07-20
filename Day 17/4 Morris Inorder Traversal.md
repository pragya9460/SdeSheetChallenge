# [Morris Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)

### Code ||

``` .cpp
class Solution {
public:
//     Morris traversal
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> in;
        if(root==NULL)  return in;
        TreeNode* cur = root;
        while(cur!=NULL){
            if(cur->left==NULL){
                in.push_back(cur->val);
                cur = cur->right;
            }
            else{
                TreeNode* prev = cur->left;
                while(prev->right!=NULL and prev->right!=cur){
                    prev = prev->right;
                }
                if(prev->right==NULL){
                    prev->right = cur;
                    cur  = cur->left;
                }
                else{
                    prev->right = NULL;
                    in.push_back(cur->val);
                    cur = cur->right;
                }
            }
        }
        return in;
    }
};
```

```
TC:- O(n) --> (O(n) + amortised O(1))
SC:- O(1)
```
