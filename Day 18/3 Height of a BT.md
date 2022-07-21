# [Height of BT](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

### Code ||

``` .cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root==NULL)  return 0;
        return max(maxDepth(root->left), maxDepth(root->right)) +1;
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
