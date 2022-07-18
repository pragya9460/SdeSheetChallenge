## [Inorder Traversal]()

### Recursive code
``` .cpp
class Solution {
public:
    void f(TreeNode* root, vector<int> &ans){
        if(root==NULL){
            return;
        }
        f(root->left, ans);
        ans.push_back(root->val);
        f(root->right, ans);
    }
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> ans;
        if(root==NULL){
            return ans;
        }
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
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> ans;
        if(root==NULL)  return ans;
        
        stack<TreeNode*> st;
        TreeNode* node = root;
        while(true){
            if(node!=NULL){
                st.push(node);
                node = node->left;
            }
            else{
                if(st.empty())  break;
                node = st.top();
                st.pop();
                ans.push_back(node->val);
                node = node->right;
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
