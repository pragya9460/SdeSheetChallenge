# [Check if given BT is Height balanced or not](https://leetcode.com/problems/balanced-binary-tree/)

### Code ||

``` .cpp
class Solution {
public:
    int f(TreeNode* root){
        if(root==NULL)  return 0;
        int lh = f(root->left);
        if(lh==-1){
            return -1;
        }
        int rh = f(root->right);
        if(rh==-1){
            return -1;
        }
        if(abs(rh-lh)>1){
            return -1;
        }
        return max(lh, rh)+1;
    }
    bool isBalanced(TreeNode* root) {
        if(root==NULL)  return true;
        return f(root)!=-1;
    }
};
```
```
TC:- O(n)
SC:- O(n)
```
