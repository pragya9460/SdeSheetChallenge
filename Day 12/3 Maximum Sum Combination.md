# [Maximum Sum Combination](https://www.interviewbit.com/problems/maximum-sum-combinations/)

### Code ||

``` .cpp
vector<int> Solution::solve(vector<int> &A, vector<int> &B, int C) {
//sort both arrays
    sort(A.begin(), A.end());
    sort(B.begin(), B.end());
    int n = A.size();
    vector<int> ans;
    //take max heap
    priority_queue<pair<int,pair<int,int>>>maxh;
    //take set
    set<pair<int,int>> st;
    //push the maximum possible sum
    maxh.push({A[n-1] + B[n-1], {n-1, n-1}});
    //store index of same
    st.insert(make_pair(n-1,n-1));
    //run loop exactly c times, every times we get a part of answer
    for(int count = 0; count < C; count++){
    //read top of max heap
        auto nd = maxh.top();
        maxh.pop();
        //here is a part of answer
        ans.push_back(nd.first);
        int i = nd.second.first;
        int j = nd.second.second;
        //taking sum of next maximum element of A keeping same element of B
        int temp1 = A[i-1] + B[j];
        if(st.find(make_pair(i-1,j)) == st.end()){
            maxh.push({temp1, {i-1,j}});
            st.insert(make_pair(i-1,j));
        }
        //taking sum of next maximum element of B keeping same element of A
        int temp2 = A[i] + B[j-1];
        if(st.find(make_pair(i,j-1)) == st.end()){
            maxh.push({temp2, {i,j-1}});
            st.insert(make_pair(i,j-1));
        }
    }
    //return answer
    return ans;
}
```

```
TC:- O(n log n)
SC:- O(2*n)
```
