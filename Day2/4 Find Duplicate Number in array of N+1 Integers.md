# [Find Duplicate Number in array of N+1 Integers](https://leetcode.com/problems/find-the-duplicate-number/)

### Code || [Notes](https://drive.google.com/file/d/1AQGezAB0lMLEOrE6bJwHYRc6k7ctLqGG/view?usp=sharing)
``` .cpp
class Solution {
public:
    int findDuplicate(vector<int>& num) {
        int s=num[0], f=num[0];
        do{
            s=num[s];
            f=num[num[f]];
        }while(s!=f);
        f=num[0];
        while(s!=f){
            s=num[s];
            f=num[f];
        }
        return s;
    }
};
```
