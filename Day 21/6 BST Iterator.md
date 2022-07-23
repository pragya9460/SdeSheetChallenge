# [BST Iterator](https://leetcode.com/problems/binary-search-tree-iterator/)

### Code ||

``` .cpp
class BSTIterator {
    private:
    stack<TreeNode*> st;
    void pushall(TreeNode* root){
        while(root!=NULL){
            st.push(root);
            root = root->left;
        }
    }
    
public:
    BSTIterator(TreeNode* root) {
        pushall(root);
    }
    
    int next() {
        TreeNode* node = st.top();
        st.pop();
        pushall(node->right);
        return node->val;
    }
    
    bool hasNext() {
        return !st.empty();
    }
};
```

```
TC:- O(1), for each function
SC:- O(log n)
```
