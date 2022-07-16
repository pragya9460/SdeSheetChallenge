# [Implement min stack](https://leetcode.com/problems/min-stack/)

### Code ||

``` .cpp
class MinStack {
    stack<long long> st;
    long long mini;
public:
    MinStack() {
        while(!st.empty()) st.pop();
        mini = INT_MAX;
    }
    
    void push(int value) {
        long long int val = value;
        if(st.empty()){
            mini = val;
            st.push(val);
        }
        else{
            if(val<mini){
                st.push(2*val*1LL - mini);
                mini = val;
            }
            else{
                st.push(val);
            }
        }
    }
    
    void pop() {
        long long int ele = st.top();
        st.pop();
        if(ele<mini){
            mini = 2*mini - ele;
        }
        
    }
    
    int top() {
        if(st.empty()) return -1;
        long long ele = st.top();
        if(ele<mini) return mini;;
        return ele;
    }
    
    int getMin() {
        return mini;
    }
};
```

```
TC:- O(1), for each function
SC:- O(n)
```
