# [Construct BST from given keys](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

### Code ||

``` .cpp
class Solution {
public:
    TreeNode* f(vector<int> &nums, int s, int e){
        if(s>e){
            return NULL;
        }
        int mid = s + (e-s)/2;
        TreeNode* root = new TreeNode(nums[mid]);
        root->left = f(nums, s, mid-1);
        root->right = f(nums, mid+1, e);
        return root;
    }
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        return f(nums, 0, nums.size()-1);
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
