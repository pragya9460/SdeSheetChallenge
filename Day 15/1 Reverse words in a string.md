# [Reverse Words in a string](https://leetcode.com/problems/reverse-words-in-a-string/)

### Code ||

``` .cpp
class Solution {
public:
    string reverseWords(string s) {
        stack<string> st;
        for(int i=0; i<s.size(); i++){
            string temp="";
            while(i<s.size() and s[i]!=' '){
                temp+=s[i];
                i++;
            }
            if(temp!="")    st.push(temp);
        }
        s="";
        while(!st.empty()){
            s+=st.top();
            st.pop();
            s+=' ';
        }
        s.pop_back();
        return s;
    }
};
```

```
TC:- O(n)
SC:- O(n)
```
