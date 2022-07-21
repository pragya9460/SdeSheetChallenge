# [Construct BT fro Postorder and Inorder](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)

### Code ||

``` .cpp
class Solution {
public:
    
    TreeNode* f(vector<int>& in, int is, int ie, vector<int>& post, int ps, int pe, unordered_map<int, int> &m){
        if(ps>pe or is>ie){
            return NULL;
        }
        TreeNode* root = new TreeNode(post[pe]);
        int inroot = m[post[pe]];
        int numleft = inroot-is;
        
        root->left = f(in, is, inroot-1, post, ps, ps+numleft-1, m);
        root->right = f(in, inroot+1, ie, post, ps+numleft, pe-1, m);
            
        return root;
    }
    
    TreeNode* buildTree(vector<int>& in, vector<int>& post) {
        if(post.size()==1){
            return new TreeNode(post[0]);
        }
        unordered_map<int, int> m;
        for(int i=0; i<post.size(); i++){
            m[in[i]]=i;
        }
        return f(in, 0, in.size()-1, post, 0, post.size()-1, m);
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
