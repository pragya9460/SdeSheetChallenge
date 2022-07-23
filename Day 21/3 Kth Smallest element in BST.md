# [Kth smallest element in BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

### Code ||

``` .cpp
class Solution {
public:
    TreeNode* f(TreeNode* root, int &k){
        if(root==NULL)  return NULL;
        TreeNode* left = f(root->left, k);
        if(left!=NULL)  return left;
        k--;
        if(k==0)    return root;
        return f(root->right, k);
    }
    int kthSmallest(TreeNode* root, int k) {
        if(root==NULL){
            return 0;
        }
        TreeNode* ans = f(root, k);
        if(ans==NULL)   return 0;
        return ans->val;
    }
};
```

```
TC:- O(n)
SC:- O(n), ---> Recursive stack space
```
