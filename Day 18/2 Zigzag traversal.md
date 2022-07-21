# [Zigzag traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

### Code ||

``` .cpp
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        vector<vector<int>> ans;
        if(root==NULL){
            return ans;
        }
        queue<TreeNode*> q;
        q.push(root);
        int tot=-1;
        while(!q.empty()){
            int n = q.size();
            vector<int> temp;
            for(int i=0; i<n; i++){
                TreeNode* node = q.front();
                q.pop();
                temp.push_back(node->val);
                if(node->left){
                    q.push(node->left);
                }
                if(node->right){
                    q.push(node->right);
                }
            }
            tot *= -1;
            if(tot==-1){
                reverse(temp.begin(), temp.end());
            }
            ans.push_back(temp);
        }
        return ans;
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
