# [Nth root of an integer](https://www.codingninjas.com/codestudio/problems/1062679?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website)

### Code ||

``` .cpp
long double power(long double mid, int n){
    long double ans = 1.0;
    while(n--)
        ans *= mid;
    return ans;
}

long double findNthRootOfM(int n, long long m) {
    long double low = 1.0, high = (long double)m, eps = 1e-9;
    while((high-low)>eps){
        long double mid = (high-low)/2.0 + low;
        if(power(mid,n)>(long double)m)
            high = mid;
        else
            low = mid;
    }
    return low;
}
```

```
TC:- O(N x log(M x 10^d) )
SC:- O(1)
```
