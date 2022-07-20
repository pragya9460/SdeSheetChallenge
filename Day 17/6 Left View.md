# [Left View](https://practice.geeksforgeeks.org/problems/left-view-of-binary-tree/1)

### Code

``` .cpp
void f(Node *root, vector<int> &ans, int level){
    if(root==NULL){
        return;
    }    
    if(ans.size()==level){
        ans.push_back(root->data);
    }
    f(root->left, ans, level+1);
    f(root->right, ans, level+1);
}

vector<int> leftView(Node *root)
{
   vector<int> ans;
   f(root, ans, 0);
   return ans;
}

```

```
TC:- O(n)
SC:- O(n), --> recursion stack space
```
