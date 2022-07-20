# [Preorder Inorder Postorder in single traversal](https://www.codingninjas.com/codestudio/problems/981269?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website)

### Code ||

``` .cpp
vector<vector<int>> getTreeTraversal(BinaryTreeNode<int> *root){
    vector<vector<int>> ans;
    if(root==NULL){
        return ans;
    }
    vector<int> in, pre, post;
    stack<pair<BinaryTreeNode<int>*, int>> st;
    st.push({root, 1});
    while(!st.empty()){
        auto it = st.top();
        st.pop();
        BinaryTreeNode<int> *cur = it.first;
        int num=it.second;
        if(num==1){
            pre.push_back(cur->data);
            num++;
            st.push({cur, num});
            if(cur->left){
                st.push({cur->left, 1});
            }
        }
        else if(num==2){
            in.push_back(cur->data);
            num++;
            st.push({cur, num});
            if(cur->right){
                st.push({cur->right, 1});
            }
        } 
        else{
            post.push_back(cur->data);
        }
    }
    ans.push_back(in);
    ans.push_back(pre);
    ans.push_back(post);
    return ans;
}
```

```
TC:-O(n)
SC:-O(n)
```
