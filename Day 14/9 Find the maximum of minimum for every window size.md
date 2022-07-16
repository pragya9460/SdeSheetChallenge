# [Find the maximum of minimum for every window size](https://practice.geeksforgeeks.org/problems/maximum-of-minimum-for-every-window-size3453/1)

### Code ||

``` .cpp
class Solution
{
    public:
    //Function to find maximum of minimums of every window size.
    vector <int> maxOfMin(int arr[], int n)
    {
        vector<int> ps(n, -1), ns(n, n);
        stack<int> st;
        
        // previous smaller;
        for(int i=0; i<n; i++){
            while (!st.empty() && arr[st.top()] >= arr[i])
                st.pop();
     
            if (!st.empty())
                ps[i] = st.top();
     
            st.push(i);
        }
        
        // empty the stack for reuse
        while(!st.empty())  st.pop();
        
        // next smaller
        for(int i=n-1; i>=0; i--){
            while (!st.empty() && arr[st.top()] >= arr[i])
                st.pop();
     
            if(!st.empty())
                ns[i] = st.top();
     
            st.push(i);
        }
        
        vector<int> ans(n+1, 0);
        
        for(int i=0; i<n; i++){
            int len = ns[i]-ps[i]-1;
            ans[len]=max(ans[len], arr[i]);
        }
        
        for (int i=n-1; i>=1; i--)
            ans[i] = max(ans[i], ans[i+1]);
            
        for(int i=0; i<n; i++){
            ans[i]=ans[i+1];
        }
        ans.pop_back();
        return ans;
    }
```

```
TC:- O(n)
SC:- O(3n)
```
