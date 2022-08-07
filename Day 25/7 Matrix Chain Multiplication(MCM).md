# [Matrix Chain Multiplication(MCM)](https://practice.geeksforgeeks.org/problems/matrix-chain-multiplication0303/1)

### Code

``` .cpp
int matrixMultiplication(int N, int arr[])
   {
       int n=N-1;
       vector<vector<int>>dp(n,vector<int>(n));
       for(int g=0;g<n;g++){
           for(int i=0,j=g;j<n;j++,i++){
               if(g==0){
                   dp[i][j]=0;
               }
               else if(g==1){
                   dp[i][j]=arr[i]*arr[j]*arr[j+1];
               }
               else{
                   int mini=INT_MAX;
                   for(int k=i;k<j;k++){
                       int left=dp[i][k];
                       int right=dp[k+1][j];
                       int mc=arr[i]*arr[k+1]*arr[j+1];
                       mini=min(mini,left+right+mc);
                   }
                   dp[i][j]=mini;
               }
           }
       }
       return dp[0][n-1];
   }
```

```
TC:-   
SC:-  
```
