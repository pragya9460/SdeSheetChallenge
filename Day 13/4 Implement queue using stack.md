# [Implement queue using stack](https://leetcode.com/problems/implement-queue-using-stacks/)

### Code ||

``` .cpp
class MyQueue {
public:
    //pop costly
    stack<int> ip, op;
    MyQueue() {
        
    }
    
    void push(int x) {
        ip.push(x);
    }
    
    int pop() {
        int t = peek();
        op.pop();
        return t;
    }
    
    int peek() {
        if(op.empty()){
            while(ip.size()){
                op.push(ip.top());
                ip.pop();
            }
        }
        return op.top();
    }
    
    bool empty() {
        return ip.empty() and op.empty();
    }
};

```
```
TC:- O(1) (O(1) amortised), pop costly
SC:- O(2n)
```
