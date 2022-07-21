# [Check if two BT are identical or not](https://leetcode.com/problems/same-tree/)

### Code ||

``` .cpp
class Solution {
public:
    bool f(TreeNode* p, TreeNode* q){
        if(p==NULL and q==NULL){
            return true;
        }
        if(p==NULL or q==NULL){
            return false;
        }
        if(p->val!=q->val){
            return false;
        }
        bool l = f(p->left, q->left);
        bool r = f(p->right, q->right);
        return l and r;
    }
    bool isSameTree(TreeNode* p, TreeNode* q) {
        return f(p, q);
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
