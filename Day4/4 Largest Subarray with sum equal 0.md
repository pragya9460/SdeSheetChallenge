# [Largest Subarray with sum equal 0](https://practice.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1)

### Code || [Notes](https://drive.google.com/file/d/1OrprSSKz6uAQqZBwZvEsTM28JRj_VTDZ/view?usp=sharing)

```.cpp
class Solution{
    public:
    int maxLen(vector<int>&a, int n)
    {   
        unordered_map<int, int> m;
        int sum=0, ans=0;
        for(int i=0; i<a.size(); i++){
            sum +=a[i];
            if(sum==0){
                ans = max(ans, i+1);
            }
            else{
                if(m.find(sum)!=m.end()){
                    ans = max(ans, i-m[sum]);
                }
                else{
                    m[sum]=i;
                }
            }
        }
        return ans;
    }
};
```
