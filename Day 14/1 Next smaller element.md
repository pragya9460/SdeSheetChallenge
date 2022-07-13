# [Next smaller element](https://www.interviewbit.com/problems/nearest-smaller-element/)

### Code ||

``` .cpp
vector<int> Solution::prevSmaller(vector<int> &a) {
    int n = a.size();
    vector<int> ans(n, -1);
    stack<int> st;
    for(int i =0; i<n; i++){
        while(!st.empty() and st.top()>=a[i])
            st.pop();
        if(i<n){
            if(!st.empty())
                ans[i] = st.top();
        }
        st.push(a[i]);
    }
    return ans;
}
```
```
TC:- O(n)
SC:- O(n)
```
