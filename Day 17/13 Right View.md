# [Right View](https://leetcode.com/problems/binary-tree-right-side-view/)

### Code ||

``` .cpp
class Solution {
public:
    void rec(TreeNode* root, int level, vector<int> & res){
        if(root==NULL) return;
        if(res.size()==level){
            res.push_back(root->val);
        }
        rec(root->right, level+1, res);
        rec(root->left, level+1, res);
    }
    vector<int> rightSideView(TreeNode* root) {
        vector <int> res;
        rec(root, 0, res);
        return res;
    }
};
```

```
TC:- O(n)
SC:- O(n), recursion stack space
```
