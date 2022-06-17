# [Job Sequencing](https://practice.geeksforgeeks.org/problems/job-sequencing-problem-1587115620/1#)

### Code ||

``` .cpp
class Solution 
{
    public:
    static bool comp(const Job a1, const Job a2){
        return (a1.profit>a2.profit);
    }
    vector<int> JobScheduling(Job arr[], int n) 
    { 
        sort(arr, arr+n, comp);
        int maxi=0;
        for(int i=0; i<n; i++){
            maxi=max(maxi, arr[i].dead);
        }
        int slot[maxi+1];
        memset(slot, -1, sizeof(slot));
        int cnt=0, pro=0;
        for(int i=0; i<n; i++){
            for(int j=arr[i].dead; j>0; j--){
                if(slot[j]==-1){
                    slot[j]=i;
                    cnt++;
                    pro+=arr[i].profit;
                    break;
                }
            }
        }
        return {cnt, pro};
    } 
};
```

```
TC:- O(nlogn) + O(n*m), where m=maxi
SC:- O(m)
```
