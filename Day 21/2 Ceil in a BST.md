# [Ceil in a BST](https://www.codingninjas.com/codestudio/problems/ceil-from-bst_920464?source=youtube&campaign=Striver_Tree_Videos&utm_source=youtube&utm_medium=affiliate&utm_campaign=Striver_Tree_Videos&leftPanelTab=0)

### Code ||

``` .cpp
int findCeil(BinaryTreeNode<int> *node, int x){
    if(node==NULL)    return 0;
    int ceil=-1;
    while(node){
        if(node->data>=x){
            ceil = node->data;
            node = node->left;
        }
        else    node = node->right;
    }
    return ceil;
}
```
```
TC:- O(log n)
SC:- O(1)
```
