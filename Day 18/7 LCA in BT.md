# [LCA in BT](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

### Code ||

``` .cpp
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==NULL){
            return root;
        }
        if(root==NULL or root==p or root==q){
            return root;
        }
        TreeNode* leftlca= lowestCommonAncestor(root->left, p, q);
        TreeNode* rightlca= lowestCommonAncestor(root->right, p, q);
        if(leftlca==NULL){
            return rightlca;
        }
        if(rightlca==NULL){
            return leftlca;
        }
        return root;
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
