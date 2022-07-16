# [LFU Cache](https://leetcode.com/problems/lfu-cache/)

### Code ||

``` .cpp
struct node{
    int key, value, cnt;
    node* next, *prev;
    node(int _key, int _value){
        key = _key;
        value = _value;
        cnt=1;
    }
};

struct listt{
    int size;
    node* head, *tail;
    listt(){
        head = new node(0, 0);
        tail = new node(0, 0);
        head->next=tail;
        tail->prev=head;
        size = 0;
    }
    void addfront(node* nod){
        node* temp = head->next;
        head->next = nod;
        nod->next = temp;
        temp->prev = nod;
        nod->prev = head;
        size++;
    }
    void removenode(node* delnode){
        node* prevnode = delnode->prev;
        node* nextnode = delnode->next;
        prevnode->next = nextnode;
        nextnode->prev = prevnode;
        size--;
    }
};

class LFUCache {
    map<int, node*> keynode;
    map<int, listt*> freqlist;
    int maxsize, minfreq, cursize;
public:
    LFUCache(int capacity) {
        maxsize=capacity;
        minfreq=0;
        cursize=0;
    }
    
    void updatefreqlist(node* nod){
        keynode.erase(nod->key);
        freqlist[nod->cnt]->removenode(nod);
        if(nod->cnt==minfreq and freqlist[nod->cnt]->size==0){
            minfreq++;
        }
        listt* nexthigherfreqlist = new listt();
        if(freqlist.find(nod->cnt+1)!=freqlist.end()){
            nexthigherfreqlist = freqlist[nod->cnt+1];
        }
        nod->cnt +=1;
        nexthigherfreqlist->addfront(nod);
        freqlist[nod->cnt] = nexthigherfreqlist;
        keynode[nod->key] = nod;
    }
    
    int get(int key) {
        if(keynode.find(key)!=keynode.end()){
            node* nod = keynode[key];
            int val = nod->value;
            updatefreqlist(nod);
            return val;
        }
        return -1;
    }
    
    void put(int key, int value) {
        if(maxsize==0)  return;
        if(keynode.find(key)!=keynode.end()){
            node* nod = keynode[key];
            nod->value = value;
            updatefreqlist(nod);
        }
        else{
            if(cursize==maxsize){
                listt* l = freqlist[minfreq];
                keynode.erase(l->tail->prev->key);
                freqlist[minfreq]->removenode(l->tail->prev);
                cursize--;
            }
            cursize++;
            minfreq=1;
            listt* listfreq  = new listt();
            if(freqlist.find(minfreq)!=freqlist.end())
                listfreq = freqlist[minfreq];
            node* nod = new node(key, value);
            listfreq->addfront(nod);
            keynode[key] = nod;
            freqlist[minfreq] = listfreq;
        }
    }
};
```

```
TC:- O(1), for each funtion
SC:- O(size)
```
