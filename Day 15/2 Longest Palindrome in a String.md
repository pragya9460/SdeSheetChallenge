# [Longest palindromic substring](https://leetcode.com/problems/longest-palindromic-substring/)

### Code ||

``` .cpp
class Solution {
public:
    string longestPalindrome(string s) {
        string ans="";
        int n = s.size();
        vector<vector<bool>> dp(n, vector<bool>(n, false));
        for(int d=0; d<n; d++){
            for(int i=0, j=d; j<n; i++, j++){
                if(d==0){
                    dp[i][j]=true;
                }
                else if(d==1){
                    if(s[i]==s[j]){
                        dp[i][j]=true;
                    }
                }
                else{
                    if(s[i]==s[j] and dp[i+1][j-1]==true){
                        dp[i][j]=true;
                    }
                }
                if(dp[i][j]==true and ans.size()<j-i+1){
                    ans = s.substr(i, j-i+1);
                }
            }
        }
        return ans;
    }
};
```

```
TC:- O(n*n)
SC:- O(n*n)
```

This problem can be done in O(n) time using Manacher's algorithm.
