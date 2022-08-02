# [Number of distinct substring in a string](https://www.codingninjas.com/codestudio/problems/count-distinct-substrings_985292?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_tries_videos&leftPanelTab=0)

### Code ||

``` .cpp
class Node{
    public:
    Node* dict[26];
    bool containsKey(char c){
        return dict[c-'a'];
    }
    void putKey(char c, Node* node){
        dict[c-'a']=node;
    }
    Node* get(char c){
        return dict[c-'a'];
    }
};
int countDistinctSubstrings(string &s){
    int cnt=0;
    Node* root = new Node();
    for(int i=0; i<s.size(); i++){
        Node* node = root;
        for(int j=i; j<s.size(); j++){
            if(!node->containsKey(s[j])){
                node->putKey(s[j], new Node());
                cnt++;
            }
            node = node->get(s[j]);
        }
    }
    return cnt+1;
}
```

```
TC:- O(n*n)
```
