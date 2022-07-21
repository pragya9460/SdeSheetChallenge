# [Construct BT from Preorder and Inorder](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

### Code ||

``` .cpp
class Solution {
public:
    TreeNode* f(vector<int>& pre, int ps, int pe, vector<int>& in, int is, int ie, unordered_map<int, int> &m){
        if(ps>pe or is>ie){
            return NULL;
        }
        TreeNode* root = new TreeNode(pre[ps]);
        int inroot= m[pre[ps]];
        int numleft = inroot-is;
        
        root->left = f(pre, ps+1, ps+numleft, in, is, inroot-1, m);
        root->right = f(pre, ps+numleft+1, pe, in, inroot+1, ie, m);
        return root;
    }
    TreeNode* buildTree(vector<int>& pre, vector<int>& in) {
        if(pre.size()==1)   return new TreeNode(pre[0]);
        unordered_map<int, int> m;
        for(int i=0; i<in.size(); i++){
            m[in[i]]=i;
        }
        return f(pre, 0, pre.size()-1, in, 0, in.size()-1, m);
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
