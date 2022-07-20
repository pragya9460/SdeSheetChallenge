# [Vertical Order Traversal](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)

### Code ||

``` .cpp
class Solution {
public:
    vector<vector<int>> verticalTraversal(TreeNode* root) {
        vector<vector<int>> ans;
        if(root==NULL)  return ans;
        map<int, map<int, multiset<int>>> m;
        queue<pair<TreeNode*, pair<int, int>>> q;
        q.push({root, {0, 0}});
        while(!q.empty()){
            auto it = q.front();
            q.pop();
            TreeNode* node = it.first;
            int col = it.second.first;
            int row = it.second.second;
            m[col][row].insert(node->val);
            if(node->left){
                q.push({node->left, {col-1, row+1}});
            }
            if(node->right){
                q.push({node->right, {col+1, row+1}});
            }
        }
        
        for(auto x: m){
            vector<int> col;
            for(auto y: x.second){
                col.insert(col.end(), y.second.begin(), y.second.end());
            }
            ans.push_back(col);
        }
        
        return ans;
    }
};
```

```
TC:- O(N*logN*logN*logN)
SC:- O(2N)
```
