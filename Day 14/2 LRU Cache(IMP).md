# [LRU Cache](https://leetcode.com/problems/lru-cache/)

### Code ||

``` .cpp
class LRUCache {
public:
    class node{
        public:
        int key, val;
        node* prev, *next;
        node(int key_, int val_){
            key = key_;
            val = val_;
        }
    };
    node* head = new node(-1, -1);
    node* tail = new node(-1, -1);
    
    int cap;
    unordered_map<int, node*> m;

    LRUCache(int capacity) {
        cap = capacity;
        head->next = tail;
        tail->prev = head;
    }
    
    void addnode(node* newnode){
        node* temp = head->next;
        head->next = newnode;
        temp->prev = newnode;
        newnode->prev = head;
        newnode->next = temp;
    }
    
    void deletenode(node* newnode){
        node* nodeprev = newnode->prev;
        node* nodenext = newnode->next;
        nodeprev->next = nodenext;
        nodenext->prev = nodeprev;
    }
    
    int get(int key) {
        if(m.find(key)!=m.end()){
            node* newnode = m[key];
            int res = newnode->val;
            deletenode(newnode);
            m.erase(key);
            addnode(newnode);
            m[key] = head->next;
            return res;
        }
        return -1;
    }
    
    void put(int key, int value) {
        if(m.find(key)!=m.end()){
            node* newnode = m[key];
            deletenode(newnode);
            m.erase(key);
        }
        if(m.size()==cap){
            m.erase(tail->prev->key);
            deletenode(tail->prev);
        }
        addnode(new node(key, value));
        m[key] = head->next;
    }
};
```

```
TC:- O(1), for each funtion
SC:- O(size)
```
