# [Minimum no. of platforms required for a railway](https://practice.geeksforgeeks.org/problems/minimum-platforms-1587115620/1#)

### Code ||

``` .cpp
class Solution{
public:
    int findPlatform(int arr[], int dep[], int n)
    {
    	sort(arr, arr+n);
    	sort(dep, dep+n);
    	int plat=1, maxi=1, i=1, j=0;
    	while(i<n and j<n){
    	    if(arr[i]<=dep[j]){
    	        plat++;
    	        i++;
    	    }
    	    else{
    	        plat--;
    	        j++;
    	    }
    	    maxi=max(maxi, plat);
    	}
    	return maxi;
    }
};
```

```
TC:- O(nlogn)
SC:- O(1)
```
