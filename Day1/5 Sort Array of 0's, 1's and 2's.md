# [Sort Array of 0's, 1's and 2's](https://leetcode.com/problems/sort-colors/)

### Code || [Notes](https://drive.google.com/file/d/11oU788HC1ucFdDqufjLX9Hv_F7E8p48b/view?usp=sharing)
``` .cpp
class Solution {
public:
    void sortColors(vector<int>& v) {
        int n = v.size();
        int l=0, m=0, h=n-1;
        while(m<=h){
            switch(v[m]){
                case 0: 
                    swap(v[l], v[m]);
                    l++;
                    m++;
                    break;
                case 1:
                    m++;
                    break;
                case 2:
                    swap(v[m], v[h]);
                    h--;
                    break;
            }
        }
    }
};
```

```
TC:- O(n)
SC:- O(1)
```
