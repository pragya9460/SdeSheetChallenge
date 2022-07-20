# [Morris Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)

### Code

``` .cpp
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> pre;
        if(root==NULL)  return pre;
        TreeNode* cur = root;
        while(cur!=NULL){
            if(cur->left==NULL){
                pre.push_back(cur->val);
                cur = cur->right;
            }
            else{
                TreeNode* prev = cur->left;
                while(prev->right!=NULL and prev->right!=cur){
                    prev = prev->right;
                }
                if(prev->right==NULL){
                    prev->right = cur;
                    pre.push_back(cur->val);
                    cur  = cur->left;
                }
                else{
                    prev->right = NULL;
                    cur = cur->right;
                }
            }
        }
        return pre;
    }
};
```

```
TC:- O(n) --> (O(n) + amortised O(1))
SC:- O(1)
```
