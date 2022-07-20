# [Max Width of BT](https://leetcode.com/problems/maximum-width-of-binary-tree/)

### Code ||

``` .cpp
class Solution {
public:
    int widthOfBinaryTree(TreeNode* root) {
        if(root==NULL){
            return 0;
        }
        long long ans=0;
        queue<pair<TreeNode*, long long>> q;
        q.push({root, 0});
        while(!q.empty()){
            long long size=q.size();
            long long mn = q.front().second;
            long long first, last;
            for(int i=0; i<size; i++){
                long long idx = q.front().second - mn;
                TreeNode* node = q.front().first;
                q.pop();
                if(i==0){
                    first = idx;
                }
                if(i==size-1){
                    last = idx;
                }
                if(node->left){
                    q.push({node->left, 2*idx});
                }
                if(node->right){
                    q.push({node->right, 2*idx+1});
                }
            }
            ans = max(ans, last-first+1);
        }
        return ans;
    }
};

```

```
TC:- O(n)
SC:- O(n)
```
