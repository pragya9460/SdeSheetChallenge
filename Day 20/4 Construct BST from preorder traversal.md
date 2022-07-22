# [Construct BST from Preorder traversal](https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/)

### Code ||

``` .cpp
class Solution {
public:
    TreeNode* f(vector<int>& pre, int &i, int &ub){
        if(i==pre.size() or pre[i]>ub){
            return NULL;
        }
        TreeNode* root = new TreeNode(pre[i++]);
        root->left = f(pre, i, root->val);
        root->right = f(pre, i, ub);
        return root;
    }
    TreeNode* bstFromPreorder(vector<int>& pre) {
        if(pre.size()==0){
            return NULL;
        }
        int i=0, ub = INT_MAX;
        return f(pre, i, ub);
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
