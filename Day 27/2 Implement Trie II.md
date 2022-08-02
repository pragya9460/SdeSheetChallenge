# [Implement Trie II](https://www.codingninjas.com/codestudio/problems/implement-trie_1387095?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website&leftPanelTab=0)

### Code ||

``` .cpp
class TrieNode{
  public:
    int wordCount, prefixCount;
    vector<TrieNode*> dict;
    TrieNode(){
        wordCount=0, prefixCount=0;
        dict.resize(26, NULL);
    }
    bool containsKey(char c){
        return (dict[c-'a']!=NULL);
    }
    void putKey(char c, TrieNode* node){
        dict[c-'a'] = node;
    }
    TrieNode* next(char c){
        return dict[c-'a'];
    }
    void increaseWordCount(){
        wordCount++;
    }
    void increasePrefixCount(){
        prefixCount++;
    }
    void decreaseWordCount(){
        wordCount--;
    }
    void decreasePrefixCount(){
        prefixCount--;
    }
    int getWordCount(){
        return wordCount;
    }
    int getPrefixCount(){
        return prefixCount;
    }
};
class Trie{
    private:
    TrieNode* root;
    public:
    Trie(){
        root = new TrieNode();
    }

    void insert(string &word){
        TrieNode* node = root;
        for(int i=0; i<word.size(); i++){
            if(!node->containsKey(word[i])){
                node->putKey(word[i], new TrieNode());
            }
            node = node->next(word[i]);
            node->increasePrefixCount();
        }
        node->increaseWordCount();
    }

    int countWordsEqualTo(string &word){
        TrieNode* node = root;
        for(int i=0; i<word.size(); i++){
            if(node->containsKey(word[i])){
                node = node->next(word[i]);
            }
            else{
                return 0;
            }
        }
        return node->getWordCount();
    }

    int countWordsStartingWith(string &word){
        TrieNode* node = root;
        for(int i=0; i<word.size(); i++){
            if(node->containsKey(word[i])){
                node = node->next(word[i]);
            }
            else{
                return 0;
            }
        }
        return node->getPrefixCount();
    }

    void erase(string &word){
        TrieNode* node = root;
        for(int i=0; i<word.size(); i++){
            if(node->containsKey(word[i])){
                node = node->next(word[i]);
                node->decreasePrefixCount();
            }
            else{
                return;
            }
        }
        node->decreaseWordCount();
    }
};

```

```
TC: O(word.size()), for each function
```
