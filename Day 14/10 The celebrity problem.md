# [The celebrity problem](https://practice.geeksforgeeks.org/problems/the-celebrity-problem/1)

### Code ||

``` .cpp
class Solution 
{
    public:
    int celebrity(vector<vector<int> >& m, int n) 
    {
        // using two pointers
        int i=0, j=n-1;
        while(i<j){
            if(m[j][i]==1)  j--;
            else    i++;
        }
        int candidate = i;
        for(int i=0; i<n; i++){
            if(i!=candidate){
                if(m[i][candidate]==0 or m[candidate][i]==1)
                    return -1;
            }
        }
        return candidate;
    }
};
```

```
TC:- O(n)
SC:- O(1)
```
