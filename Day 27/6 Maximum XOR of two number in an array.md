# [Maximum XOR of two number in an array](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/)

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
    int findMaximumXOR(vector<int>& a) {
        Trie trie;
        int maxi=0;
        for(auto it: a)    trie.insert(it);
        for(auto it: a){
            maxi = max(maxi, trie.getMax(it));
        }
        return maxi;
    }
};
```

```
TC:- O(n*32)
```
