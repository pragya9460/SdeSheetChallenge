# [Implement Trie](https://leetcode.com/problems/implement-trie-prefix-tree/)

### Code ||
``` .cpp
class TrieNode{
  public:
    vector<TrieNode*> dict;
    bool isEnd;
    TrieNode(){
        isEnd = false;
        dict.resize(26, nullptr);
    }
    bool containKey(char c){
        return (dict[c-'a']!=NULL);
    }
    void putKey(char c, TrieNode* node){
        dict[c-'a'] = node;
    }
    TrieNode* next(char c){
        return dict[c-'a'];
    }
    void setEnd(){
        isEnd = true;
    }
    bool getEnd(){
        return isEnd;
    }
};
class Trie {
public:
    TrieNode* root;
    Trie() {
        root = new TrieNode();
    }
    
    void insert(string s) {
        TrieNode* node = root;
        for(int i=0;i<s.length();i++){
            if(!node->containKey(s[i])){
                node->putKey(s[i], new TrieNode());
            }
            node = node->next(s[i]);
        }
        node->setEnd();
    }
    
    bool search(string s) {
        TrieNode* node = root;
        for(int i=0;i<s.length();i++){
            if(!node->containKey(s[i]))
                return false;
            node = node->next(s[i]);
        }
        return node->getEnd();
    }
    
    bool startsWith(string s) {
        TrieNode* node = root;
        for(int i=0;i<s.length();i++){
            if(!node->containKey(s[i]))
                return false;
            node = node->next(s[i]);
        }
        return true;
    }
};
```

```
TC:- O(word.size()) for each function
```
