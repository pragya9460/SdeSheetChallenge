# [3 sum](https://leetcode.com/problems/3sum/)

### Code ||

``` .cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& v) {
        vector<vector<int>> res;
        sort(begin(v), end(v));
        if(v.empty())
            return res;
        int target = 0;
        int n = v.size();
        for(int i=0; i<n; i++){
            int target2 = target -v[i];
            int front = i+1;
            int end = n-1;
            while(front<end){
                int twosum = v[front] + v[end];
                if(twosum<target2)
                    front++;
                else if(twosum>target2)
                    end--;
                else{
                    vector<int> triplet(3, 0);
                    triplet[0]=v[i];
                    triplet[1]=v[front];
                    triplet[2]=v[end];
                    res.push_back(triplet);
                    
                    while(front<end and v[front]==triplet[1])
                        ++front;
                    
                    while(front<end and v[end]==triplet[2])
                        --end;
                }
            }
            while(i+1<n and v[i]==v[i+1])
                ++i;
        }
        return res;
    }
};
```
