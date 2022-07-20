# [Top View](https://practice.geeksforgeeks.org/problems/top-view-of-binary-tree/1)

### Code ||

``` .cpp
class Solution
{
    public:
    vector<int> topView(Node *root)
    {
        vector<int> ans;
        if(root==NULL)  return ans;
        map<int, int> m;
        queue<pair<Node*, int>> q;
        q.push({root, 0});
        while(!q.empty()){
            auto it= q.front();
            q.pop();
            Node* node = it.first;
            int line = it.second;
            if(m.find(line)==m.end()){
                m[line] = node->data;
            }
            if(node->left){
                q.push({node->left, line-1});
            }
            if(node->right){
                q.push({node->right, line+1});
            }
            
        }
        for(auto it: m){
            ans.push_back(it.second);
        }
        return ans;
    }

};
```

```
TC:- O(n)
SC:- O(2n) --> for map and queue
```
