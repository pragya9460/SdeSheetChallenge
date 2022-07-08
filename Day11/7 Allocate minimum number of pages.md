# [Allocate Minimum number of pages](https://www.interviewbit.com/problems/allocate-books/)

### Code ||

``` .cpp
bool isPos(int mid, vector<int> &a, int s){
    int stu=1, pages=0;
    for(int i=0; i<a.size(); i++){
        if(a[i]>mid){
            return false;
        }
        if(pages+a[i]>mid){
            stu++;
            pages = a[i];
        }
        else{
            pages+=a[i];
        }
    }
    if(stu>s){
        return false;
    }
    return true;
}
int Solution::books(vector<int> &a, int s) {
    if(s>a.size()){
        return -1;
    }
    int l = a[0], h=0, res=-1;
    for(int i=0; i<a.size(); i++){
        l = min(l, a[i]);
        h +=a[i];
    }
    while(l<=h){
        int m = (l+h)>>1;
        if(isPos(m, a, s)){
            res = m;
            h = m-1;
        }
        else{
            l = m+1;
        }
    }
    return res;
}

```

```
TC:- O(nlog n)
SC:- O(1)
```
