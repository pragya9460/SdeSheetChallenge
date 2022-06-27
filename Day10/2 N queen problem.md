# [N queen problem](https://leetcode.com/problems/n-queens/)

### Code ||

``` .cpp
class Solution {
public:
    //using hashing, 
    // TC:- O(n! * n)
    // SC:- O(6n)
    void f(int col, int n, vector<vector<string>> &ans, vector<string> &b, vector<int> &lr, vector<int> &ld, vector<int> &ud){
        if(col==n){
            ans.push_back(b);
            return;
        }
        for(int i=0; i<n; i++){
            if(lr[i]==0 and ld[i+col]==0 and ud[n-1 + col - i]==0){
                b[i][col]='Q';
                lr[i]=1;
                ld[i+col]=1;
                ud[n-1 + col-i]=1;
                f(col+1, n, ans, b, lr, ld, ud);
                b[i][col]='.';
                lr[i]=0;
                ld[i+col]=0;
                ud[n-1 + col-i]=0;
            }
        }
    }
    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> ans;
        string s(n, '.');
        vector<string> b(n);
        for(int i=0; i<n; i++){
            b[i]=s;
        }
        vector<int> lr(n, 0), ld(2*n-1, 0), up(2*n-1, 0);
        f(0, n, ans, b, lr, ld, up);
        return ans;
    }
};

/*
// TC:- O(n! * n * n)
// SC: O(n)
class Solution {
public:
    bool isSafe(int row, int col, int n, vector<string> &b){
        int drow=row, dcol=col;
        while(row>=0 and col>=0){
            if(b[row][col]=='Q'){
                return false;
            }
            row--;
            col--;
        }
        
        row=drow, col=dcol;
        while(col>=0){
            if(b[row][col]=='Q'){
                return false;
            }
            col--;
        }
        
        row=drow, col=dcol;
        while(col>=0 and row<n){
            if(b[row][col]=='Q'){
                return false;
            }
            col--, row++;
        }
        return true;
    }
    void f(int col, int n, vector<vector<string>> &ans, vector<string> &b){
        if(col==n){
            ans.push_back(b);
            return;
        }
        for(int i=0; i<n; i++){
            if(isSafe(i, col, n, b)){
                b[i][col]='Q';
                f(col+1, n, ans, b);
                b[i][col]='.';
            }
        }
    }
    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> ans;
        string s(n, '.');
        vector<string> b(n);
        for(int i=0; i<n; i++){
            b[i]=s;
        }
        f(0, n, ans, b);
        return ans;
    }
};

*/
```
