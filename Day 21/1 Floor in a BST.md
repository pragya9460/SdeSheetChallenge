# [Floor in a BST](https://www.codingninjas.com/codestudio/problems/floor-from-bst_920457?source=youtube&campaign=Striver_Tree_Videos&utm_source=youtube&utm_medium=affiliate&utm_campaign=Striver_Tree_Videos&leftPanelTab=0)

### Code ||

``` .cpp
int floorInBST(TreeNode<int> * root, int x){
    if(root==NULL)    return 0;
    int floor;
    while(root){
        if(root->val<=x){
            floor = root->val;
            root = root->right;
        }
        else    root = root->left;
    }
    return floor;
}
```

```
TC:- O(log n)
SC:- O(1)
```
