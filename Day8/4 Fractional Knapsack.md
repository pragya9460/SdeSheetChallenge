# [Fractional Knapsack](https://practice.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1)

### Code ||

``` .cpp
class Solution
{
    public:
    static bool comp(const Item a, const Item b){
        double r1 = (double)a.value/(double)a.weight;
        double r2 = (double)b.value/(double)b.weight;
        return r1>r2;
    }
    double fractionalKnapsack(int W, Item arr[], int n)
    {
        sort(arr, arr+n, comp);
        int curw=0;
        double ans=0.0;
        for(int i=0; i<n; i++){
            if(curw+arr[i].weight<=W){
                curw+=arr[i].weight;
                ans+=arr[i].value;
            }
            else{
                int remain = W-curw;
                ans+=(arr[i].value/(double)arr[i].weight)*(double)remain;
                break;
            }
        }
        return ans;
    }
        
};
```

```
TC:- O(nlogn)
SC:- O(1)
```
