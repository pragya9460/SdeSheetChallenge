# [Subset Sum](https://practice.geeksforgeeks.org/problems/subset-sums2234/1)

### Code ||

``` .cpp
class Solution{
public:
    void f(vector<int> &arr, int i, int sum, vector<int> &ans, int n){
        if(i==n){
            ans.push_back(sum);
            return;
        }
        f(arr, i+1, sum, ans, n);
        f(arr, i+1, sum+arr[i], ans, n);
    }
    vector<int> subsetSums(vector<int> arr, int n)
    {
        vector<int> ans;
        f(arr, 0, 0, ans, n);
        return ans;
    }
};

```

```
TC:- O(2^n)
SC:- O(2^n)
```
