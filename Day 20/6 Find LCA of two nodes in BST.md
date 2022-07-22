# [Find LCA of two nodes in BST](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

### Code ||

``` .cpp
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==NULL){
            return NULL;
        }
        if(p->val<root->val and q->val<root->val){
            return lowestCommonAncestor(root->left, p, q);
        }
        if(p->val>root->val and q->val>root->val){
            return lowestCommonAncestor(root->right, p, q);
        }
        return root;
    }
};
```

```
TC:- O(log n)
SC:- O(log n) ---> recursion stack space
```
