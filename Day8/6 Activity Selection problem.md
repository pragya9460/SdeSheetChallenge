# [Activity selection problem](https://practice.geeksforgeeks.org/problems/activity-selection-1587115620/1#)

### Code ||

``` .cpp
class Solution
{
    public:
    struct act{
        int s,e, pos;  
    };
    static bool comp(const act a, const act b){
        if(a.e<b.e) return true;
        else if(a.e>b.e)    return false;
        else if(a.pos<b.pos)    return true;
        return false;
    }
    int activitySelection(vector<int> start, vector<int> end, int n)
    {
        struct act a[n];
        for(int i=0; i<n; i++){
            a[i].s=start[i];
            a[i].e=end[i];
            a[i].pos=i+1;
        }
        sort(a, a+n, comp);
        int cnt=1;
        int lim=a[0].e;
        for(int i=1; i<n; i++){
            if(a[i].s>lim){
                cnt++;
                lim=a[i].e;
            }
        }
        return cnt;
    }
};
```

```
TC:- O(nlogn)
SC:- O(1)
```
