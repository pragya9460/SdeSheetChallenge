# [Stock span problem](https://leetcode.com/problems/online-stock-span/)

### Code ||

``` .cpp
class StockSpanner {
public:
    int size = 100000;
    stack<int> st;
    vector<int> v;
    int ind;
    StockSpanner() {
        ind=0;
        v.resize(size);
    }
    
    int next(int price) {
        int ans;
        if(st.empty()){
            v[ind]=price;
            ans=ind+1;
            st.push(ind);
        }
        else{
            v[ind]=price;
            while(!st.empty() and v[st.top()]<=v[ind])  st.pop();
            if(st.empty())  ans=ind+1;
            else    ans= ind-st.top();
            st.push(ind);
        }
        ind++;
        return ans;
    }
};
```
```
TC:- O(n)
SC:- O(n)
```
