# [Check for balances parentheses](https://leetcode.com/problems/valid-parentheses/)

### Code ||

``` .cpp
class Solution {
public:
    bool isValid(string s) {
        int n=s.length();
        if(n%2==1)
            return false;
        stack<char> st;
        int i=0;
        while(i<n){
            if(!st.empty() && (st.top()-s[i]==-1 || st.top()-s[i]==-2)){
                st.pop();
            }
            else{
                st.push(s[i]);
            }
            i++;
        }
        return st.empty();
    }
};
```

```
TC:- O(n)
SC:-O(n)
```
