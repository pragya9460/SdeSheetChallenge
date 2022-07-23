# [Distinct Numbers in a window](https://www.interviewbit.com/problems/distinct-numbers-in-window/)

### Code ||

``` ..cpp
vector<int> Solution::dNums(vector<int> &a, int b) {
    unordered_map<int, int> m;
    vector<int> ans;
    for(int i=0; i<b; i++){
        m[a[i]]++;
    }
    for(int i=b;i<a.size();i++){
        ans.push_back(m.size());
        m[a[i-b]]--;
        if(m[a[i-b]]==0) m.erase(a[i-b]);
        m[a[i]]++;
    }
    ans.push_back(m.size());
    return ans;
}
```

```
TC:- O(n)
SC:- O(n)
```
