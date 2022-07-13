# [Implement stack using queues](https://leetcode.com/problems/implement-stack-using-queues/)

### Code ||

``` .cpp
class MyStack {
public:
    queue<int> q;
    MyStack() {
        
    }
    
    void push(int x) {
        q.push(x);
        for(int i=1; i<q.size(); i++){
            q.push(q.front());
            q.pop();
        }
    }
    
    int pop() {
        int t = q.front();
        q.pop();
        return t;
    }
    
    int top() {
        return q.front();
    }
    
    bool empty() {
        if(q.size()==0){
            return true;
        }
        return false;
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
