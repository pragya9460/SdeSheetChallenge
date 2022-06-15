# [Count number of subarrays with given xor k](https://www.interviewbit.com/problems/subarray-with-given-xor/)

### Code || [Notes](https://drive.google.com/file/d/1Oz5nubp-6IcqYUShpbcW8V1gSIq7pGD2/view?usp=sharing)
``` .cpp
int Solution::solve(vector<int> &a, int B) {
    unordered_map<int, int> m;
    int xorr=0, cnt=0;
    for(auto it: a){
        xorr^=it;
        if(xorr==B){
            cnt++;
        }
        if(m.find(xorr^B)!=m.end()){
            cnt+= m[xorr^B];
        }
        m[xorr]++;
    }
    return cnt;
}

```

```
TC:- O(nlogn)
SC:- O(n)
```
