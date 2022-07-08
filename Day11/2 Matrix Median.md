# [Matrix Median](https://www.interviewbit.com/problems/matrix-median/)

### Code ||

``` .cpp
int Solution::findMedian(vector<vector<int> > &A) {
    int l = INT_MAX, r=0; 
    for(int i=0; i<A.size(); i++){
        l = min(l, A[i][0]);
        r = max(r, A[i][A[0].size()-1]);
    }
    int mid, req = (int)A.size() * (int)A[0].size();
    while(l<r){
        mid = l + (r - l) / 2;
        int cnt = 0;
        for(auto &i: A){ 
            //using upper bound in a sorted array to count number of elements smaller than mid
            int p = upper_bound(i.begin(), i.end(), mid) - i.begin();
            // cout<<p<<" ";
            cnt += p;
        }
        if(cnt >= (req+1)/2) r = mid;
        else l = mid+1;
    }   
    return l;
}
```

```
TC:- O(log(mx) * n * log(m))  , mx = max of element's in matrix, n = no. of rows, m = no. of colomns.
log(mx) -> for Binary Search
log(m) -> for upper_bound
n*log(m) -> for applying upper bound in every row
SC:- O(1)
```
