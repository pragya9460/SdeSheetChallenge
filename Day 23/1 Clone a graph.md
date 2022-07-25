# [Clone a Graph](https://leetcode.com/problems/clone-graph/)

### Code ||

``` .cpp
class Solution {
public:
    Node* dfs(Node* node, unordered_map<Node*, Node*> &m){
        vector<Node*> nb;
        Node* clone = new Node(node->val);
        m[node] = clone;
        for(auto it: node->neighbors){
            if(m.find(it)!= m.end()){
                nb.push_back(m[it]);
            }
            else{
                nb.push_back(dfs(it, m));
            }
        }
        clone->neighbors = nb;
        return clone;
    }
    Node* cloneGraph(Node* node) {
        if(node==NULL)  return NULL;
        if(node->neighbors.size()==0)   return new Node(node->val);
        unordered_map<Node*, Node*> m;
        return dfs(node, m);
    }
};
```

```
TC:- O(N+E)
SC:- O(N) --> for map DS
```
