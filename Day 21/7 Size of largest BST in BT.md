# [Size of largest BST in BT](https://practice.geeksforgeeks.org/problems/largest-bst/1)

### Code |

``` .cpp
class nodevalue{
    public:
    int mn, mx, mxsize;
    nodevalue(int mn, int mx, int mxsize){
        this->mn = mn;
        this->mx = mx;
        this->mxsize = mxsize;
    }
};

class Solution{
    public:
    nodevalue f(Node* root){
        if(root==NULL)  return nodevalue(INT_MAX, INT_MIN, 0);
        auto left = f(root->left);
        auto right = f(root->right);
        
        if(left.mx < root->data and root->data < right.mn){
            return nodevalue(min(root->data, left.mn), max(root->data, right.mx), left.mxsize+ right.mxsize+ 1);
        }
        return nodevalue(INT_MIN, INT_MAX, max(left.mxsize, right.mxsize));
    }
    int largestBst(Node *root){
    	return f(root).mxsize;
    }
};
```

```
TC:- O(n)
SC:- O(1)
```
