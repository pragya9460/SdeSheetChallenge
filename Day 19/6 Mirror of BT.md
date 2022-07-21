# [Mirror of BT](https://practice.geeksforgeeks.org/problems/mirror-tree/1)

### Code ||

``` .cpp
class Solution {
  public:
    void mirror(Node* root) {
         if(root==NULL){
             return;
         }
         queue<Node*> q;
         q.push(root);
         while(!q.empty()){
             int n = q.size();
             for(int i=0; i<n; i++){
                 Node* node = q.front();
                 q.pop();
                 if(node->left){
                     q.push(node->left);
                 }
                 if(node->right){
                     q.push(node->right);
                 }
                 Node* temp = node->left;
                 node->left = node->right;
                 node->right = temp;
             }
         }
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
