# [Populate Next Right pointers of Tree](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

### Code ||

``` .cpp
class Solution {
public:
    Node* connect(Node* root) {
        if(root==NULL){
            return root;
        }
        Node* temp=root;
        while(temp->left!=NULL and temp->right!=NULL){
            Node* cur = temp;
            while(true){
                cur->left->next=cur->right;
                if(cur->next==NULL){
                    break;
                }
                cur->right->next = cur->next->left;
                cur = cur->next;
            }
            temp = temp->left;
        }
        return root;
    }
};
```
```
TC:- O(n)
SC:- O(1)
```
