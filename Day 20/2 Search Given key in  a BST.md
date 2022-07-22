# [Search Given Key in BST](https://leetcode.com/problems/search-in-a-binary-search-tree/)

### Code ||

``` .cpp
class Solution {
public:
    TreeNode* searchBST(TreeNode* root, int v) {
        if(root==NULL){
            return root;
        }
        while(root!=NULL){
            if(root->val==v){
                return root;
            }
            else if(root->val>v){
                root = root->left;
            }
            else{
                root = root->right;
            }
        }
        return NULL;
    }
};
```

```
TC:- O(log n)
SC:- O(1)
```
