# [Boundary Traversal in BT](https://practice.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1)

### Code ||

``` .cpp
class Solution {
public:
    bool isleaf(Node* root){
        if(root->left==NULL and root->right==NULL)  return true;
        return false;
    }
    
    void leftB(Node* root, vector<int> &ans){
        Node* cur = root->left;
        while(cur){
            if(!isleaf(cur)){
                ans.push_back(cur->data);
            }
            if(cur->left)   cur = cur->left;
            else    cur = cur->right;
        }
    }
    
    void rightB(Node* root, vector<int> &ans){
        Node* cur = root->right;
        vector<int> temp;
        while(cur){
            if(!isleaf(cur)){
                temp.push_back(cur->data);
            }
            if(cur->right)  cur= cur->right;
            else    cur = cur->left;
        }
        reverse(temp.begin(), temp.end());
        ans.insert(ans.end(), temp.begin(), temp.end());
    }
    
    void pre(Node* root, vector<int> &ans){
        if(isleaf(root)){
            ans.push_back(root->data);
            return;
        }
        if(root->left){
            pre(root->left, ans);
        }
        if(root->right){
            pre(root->right, ans);
        }
    }
    vector <int> boundary(Node *root)
    {
        vector<int> ans;
        if(root==NULL){
            return ans;
        }
        if(!isleaf(root))   ans.push_back(root->data);
        leftB(root, ans);
        pre(root, ans);
        rightB(root, ans);
        return ans;
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
