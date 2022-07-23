# [Kth largest element](https://practice.geeksforgeeks.org/problems/kth-largest-element-in-bst/1)

### Code ||

``` .cpp
class Solution
{
    public:
    Node* f(Node* root, int &k){
        if(root==NULL)  return NULL;
        Node* left = f(root->right, k);
        if(left!=NULL)  return left;
        k--;
        if(k==0)    return root;
        return f(root->left, k);
    }
    int kthLargest(Node *root, int k){
        if(root==NULL){
            return 0;
        }
        Node* ans = f(root, k);
        if(ans==NULL)   return 0;
        return ans->data;
    }
};
```

```
TC:- O(log n)
SC:- O(log n)
```
