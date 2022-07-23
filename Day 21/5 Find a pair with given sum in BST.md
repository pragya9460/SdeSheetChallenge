# [Find a pair with given sum in BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)

### Code(Not that optimal) || 

``` .cpp
class Solution {
public:
    void inorder(TreeNode* root, vector <int> &v){
        if(root==NULL){
            return;
        }
        inorder(root->left, v);
        v.push_back(root->val);
        inorder(root->right, v);
    }
    bool findTarget(TreeNode* root, int k) {
        if(root->left==NULL and root->right==NULL){
            return false;
        } 
        vector<int> in;
        inorder(root, in);
        int i=0, j=in.size()-1;
        while(i<j){
            long long int sum = (long)in[i] + (long)in[j];
            if(sum==k){
                return true;
            }
            else if(sum<k){
                i++;
            }
            else{
                j--;
            }
        }
        return false;
    }
};
```

```
TC:- O(n)
SC:- O(n)
```


### Code(Most Optimal) ||

``` .cpp
class BSTIterator{
  public:
    stack<TreeNode*> st;
    bool reverse;
    BSTIterator(TreeNode* root, bool isreverse){
        reverse = isreverse;
        pushall(root);
    }
    void pushall(TreeNode* node){
        while(node!=NULL){
            st.push(node);
            if(reverse) node = node->right;
            else    node = node->left;
        }
    }
    bool hasNext(){
        return !st.empty();
    }
    int next(){
        TreeNode* root = st.top();
        st.pop();
        if(reverse) pushall(root->left);
        else    pushall(root->right);
        return root->val;
    }
};

class Solution {
public:
    bool findTarget(TreeNode* root, int k) {
        if(root==NULL)  return false;
        BSTIterator* l = new BSTIterator(root, false);
        BSTIterator* r = new BSTIterator(root, true);
        int i = l->next();
        int j = r->next();
        while(i<j){
            if(i+j==k)  return true;
            else if(i+j<k)  i = l->next();
            else    j = r->next();
        }
        return false;
    }
};
```

```
TC:- O(n)
SC:- O(log n) , i.e height of the tree
```
