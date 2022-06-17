# [N meeting in a room](https://practice.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1)

### Code ||

``` .cpp
class Solution{
public:
    struct meeting{
      int start, end, pos;  
    };
    static bool comp(struct meeting m1, struct meeting m2){
        if(m1.end<m2.end)   return true;
        else if(m1.end>m2.end)  return false;
        else if(m1.pos<m2.pos)  return true;
        return false;
    }
    int maxMeetings(int s[], int e[], int n)
    {
        struct meeting meet[n];
        for(int i=0; i<n; i++){
            meet[i].start = s[i];
            meet[i].end = e[i];
            meet[i].pos = i+1;
        }
        sort(meet, meet+n, comp);
        int cnt=1;
        int lim = meet[0].end;
        for(int i=1; i<n; i++){
            if(meet[i].start>lim){
                cnt++;
                lim = meet[i].end;
            }
        }
        return cnt;
    }
};
```

```
TC:- O(nlogn)
SC:- O(n)
```
