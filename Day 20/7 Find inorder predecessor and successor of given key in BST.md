# [Find inorder predecessor and successor of given key in BST](https://practice.geeksforgeeks.org/problems/predecessor-and-successor/1)

### Code ||

``` .cpp
Node* p(Node* root, int key){
    Node* pre = NULL;
    while(root!=NULL){
        if(root->key>=key){
            root = root->left;
        }
        else{
            pre = root;
            root = root->right;
        }
    }
    return pre;
}

Node* s(Node* root, int key){
    Node* suc = NULL;
    while(root!=NULL){
        if(root->key>key){
            suc = root;
            root = root->left;
        }
        else{
            root = root->right;
        }
    }
    return suc;
}

void findPreSuc(Node* root, Node*& pre, Node*& suc, int key)
{
    if(root==NULL){
        pre = suc = NULL;
        return;
    }
    pre = p(root, key);
    suc = s(root, key);
}
```

```
TC:- O(log n)
SC:- O(1)
```
