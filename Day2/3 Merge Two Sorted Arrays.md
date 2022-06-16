# [Merge Two Sorted Arrays](https://leetcode.com/problems/merge-sorted-array/)

### Code || [Notes](https://drive.google.com/file/d/1Y6md1TBhr-hDPMyynHJkosUbuP7cXS4u/view?usp=sharing)

``` .cpp
class Solution {
public:
//     Using Gap Fill method
    void merge(vector<int>& v1, int m, vector<int>& v2, int n) {
        int gap = ceil((float)(m+n)/2);
        int i, j;
        while(gap>0){
            i=0, j=gap;
            while(j<(m+n)){
                if(j<m and v1[i]>v1[j]){
                    swap(v1[i], v1[j]);
                }
                else if(i<m and j>=m and v1[i]>v2[j-m]){
                    swap(v1[i], v2[j-m]);
                }
                else if(i>=m and j>=m and v2[i-m]>v2[j-m]){
                    swap(v2[i-m], v2[j-m]);
                }
                i++; j++;
            }
            if(gap==1)  gap=0;
            else     gap = ceil((float)gap/2);
        }
        for(int i=m; i<m+n; i++){
            v1[i]=v2[i-m];
        }
    }
};

```

```
TC:- O(Logn)
SC:- O(1)
```
