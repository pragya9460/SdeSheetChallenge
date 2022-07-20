# [Root to Node path](https://www.interviewbit.com/problems/path-to-given-node/)

### Code ||

``` .cpp
 bool f(TreeNode* root, int b, vector<int> &ans){
    if(root==NULL){
        return false;
    }
    ans.push_back(root->val);
    if(root->val==b){
        return true;
    }
    if(f(root->left, b, ans) or f(root->right, b, ans)){
        return true;
    }
    ans.pop_back();
    return false;
 }
 
vector<int> Solution::solve(TreeNode* a, int b) {
    vector<int> ans;
    if(a==NULL){
        return ans;
    }
    if(a->val==b){
        return {b};
    }
    f(a, b, ans);
    return ans;
}
```

```
TC:- O(n)
SC:- O(n), recursion stack space
```
