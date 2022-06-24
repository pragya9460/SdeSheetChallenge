# [Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/)

### Code ||

``` .cpp
class Solution {
public:
    bool isPalindrome(string s, int start, int end){
        while(start<=end){
            if(s[start++]!=s[end--]){
                return false;
            }
        }
        return true;
    }
    void func(int index, string s, vector<vector<string>> &res, vector <string> &path){
        if(index==s.size()){
            res.push_back(path);
            return;
        }
        for(int i=index; i<s.size(); i++){
            if(isPalindrome(s, index, i)){
                path.push_back(s.substr(index, i-index+1));
                func(i+1, s, res, path);
                path.pop_back();
            }
        }
    }
    vector<vector<string>> partition(string s) {
        vector <vector <string>> res;
        vector <string> path;
        func(0, s, res, path);
        return res;
    }
};
```

```
TC:- O(2^n * k * (n/2))
SC:- O(k*x)
```
