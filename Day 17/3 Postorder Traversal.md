# [Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)

### Recursive code

``` .cpp
class Solution {
public:
    void post(TreeNode* root, vector<int> &ans){
        if(root==NULL){
            return;;
        }
        post(root->left, ans);
        post(root->right, ans);
        ans.push_back(root->val);
    }
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> ans;
        if(root==NULL)  return ans;
        
        post(root, ans);
        return ans;
    }
};
```
```
TC:- O(n)
SC:- O(h), h is height of tree, recursion stack space 
```


### Iterative Code (Using two stack)
``` .cpp
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
          vector<int> v;
        if(!root)return v;
        stack<TreeNode*> st1;
        stack<TreeNode*> st2;
        
        st1.push(root);
        while(!st1.empty()){
            TreeNode* node=st1.top();
            st1.pop();
            st2.push(node);
            if(node->left)st1.push(node->left);
            if(node->right)st1.push(node->right);
        }
        while(!st2.empty()){
            v.push_back(st2.top()->val);
            st2.pop();
        }
       return v;
    }
};
```
```
TC:- O(n)
SC:- O(2n)
```

### Iterative Code (Using one stack)
``` .cpp
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> ans;
        if(root==NULL)return ans;
        stack<TreeNode*> st;
        TreeNode* node = root;
        while(node!=NULL or !st.empty()){
            if(node!=NULL){
                st.push(node);
                node = node->left;
            }
            else{ 
                TreeNode* temp = st.top()->right;
                if(temp==NULL){
                    temp = st.top();
                    st.pop();
                    ans.push_back(temp->val);
                    while(!st.empty() and temp==st.top()->right){
                        temp = st.top();
                        st.pop();
                        ans.push_back(temp->val);
                    }
                }
                else{
                    node = temp;
                }
            }
        }
       return ans;
    }
};
```
```
TC:- O(n)
SC:- O(n)
```
