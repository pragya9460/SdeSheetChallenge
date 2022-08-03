# [Maximum XOR With an Element From Array](https://leetcode.com/problems/maximum-xor-with-an-element-from-array/)

### Code ||

``` .cpp
struct Node{
    Node* dict[2];
    bool containsKey(int bit){
        return (dict[bit]!=NULL);
    }
    void putKey(int bit, Node* node){
        dict[bit]=node;
    }
    Node* get(int bit){
        return dict[bit];
    }
};

class Trie{
  private: 
    Node* root;
  public:
    Trie(){
        root = new Node();
    }
    void insert(int num){
        Node* node = root;
        for(int i=31; i>=0; i--){
            int bit = (num>>i)&1;
            if(!node->containsKey(bit)){
                node->putKey(bit, new Node());
            }
            node = node->get(bit);
        }
    }
    
    int getMax(int num){
        Node* node = root;
        int maxNum=0;
        for(int i=31; i>=0; i--){
            int bit = (num>>i)&1;
            if(node->containsKey(1-bit)){
                maxNum = maxNum | (1<<i);
                node = node->get(1-bit);
            }
            else{
                 node = node->get(bit);
            }
        }
        return maxNum;
    }
};

class Solution {
public:
    vector<int> maximizeXor(vector<int>& arr, vector<vector<int>>& queries) {
        int n = arr.size();
        sort(arr.begin(), arr.end()); // O(n log n)
        vector<pair<int, pair<int, int>>> oQ;
        int q = queries.size();
        for(int i=0; i<q; i++){
            oQ.push_back({queries[i][1], {queries[i][0], i}});
        }
        sort(oQ.begin(), oQ.end()); // O(q log q)
        vector<int> ans(q, 0);
        int ind=0;
        Trie trie;
        for(int i=0; i<q; i++){
            int ai = oQ[i].first;
            int xi = oQ[i].second.first;
            int qInd = oQ[i].second.second;
            while(ind<n and arr[ind]<=ai){
                trie.insert(arr[ind]);
                ind++;
            }
            if(ind==0)    ans[qInd] = -1;
            else     ans[qInd] = trie.getMax(xi);
        }
        return ans;
    }
};
```

```
TC:- O(q*32 + n*32)
```
