# [Bottom View](https://practice.geeksforgeeks.org/problems/bottom-view-of-binary-tree/1)

### Code ||

``` .cpp
class Solution {
  public:
    vector <int> bottomView(Node *root) {
        vector<int> ans;
        if(root==NULL)  return ans;
        map<int, int> m;
        queue<pair<Node*, int>> q;
        q.push({root, 0});
        while(!q.empty()){
            auto it= q.front();
            q.pop();
            Node* nod = it.first;
            int line = it.second;
            m[line] = nod->data;
            if(nod->left){
                q.push({nod->left, line-1});
            }
            if(nod->right){
                q.push({nod->right, line+1});
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

