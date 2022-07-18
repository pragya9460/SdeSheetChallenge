# [Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)

### Recursive code
``` .cpp
class Solution {
public:
    void f(TreeNode* root, vector<int> &ans){
        if(root==NULL)  return;
        ans.push_back(root->val);
        f(root->left, ans);
        f(root->right, ans);
    }
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> ans;
        if(root==NULL)  return ans;
        f(root, ans);
        return ans;
    }
};
```
```
TC:- O(n)
SC:- O(h), h is height of tree, recursion stack space 
```


### Iterative Code
``` .cpp
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> ans;
        if(root==NULL)  return ans;
        
        stack<TreeNode*> st;
        st.push(root);
        while(!st.empty()){
            TreeNode* node = st.top();
            st.pop();
            ans.push_back(node->val);
            if(node->right){
                st.push(node->right);
            }
            if(node->left){
                st.push(node->left);
            }
        }
        return ans;
    }
};
```
```
TC:- O(n)
SC:- O(h), where h is height of the tree
```
