# [Inversion of Array](https://practice.geeksforgeeks.org/problems/inversion-of-array-1587115620/1/)

### Code || [Notes](https://drive.google.com/file/d/1F8e4D4vQpqpWCkANr-_Hc9z0WTTILYdc/view?usp=sharing)

``` .cpp
long long merge(long long arr[],long long temp[],long long left,long long mid,long long right)
{
    long long inv_count=0;
    long long i = left;
    long long j = mid;
    long long k = left;
    while((i <= mid-1) && (j <= right)){
        if(arr[i] <= arr[j]){
            temp[k++] = arr[i++];
        }
        else
        {
            temp[k++] = arr[j++];
            inv_count = inv_count + (mid - i);
        }
    }

    while(i <= mid - 1)
        temp[k++] = arr[i++];

    while(j <= right)
        temp[k++] = arr[j++];

    for(i = left ; i <= right ; i++)
        arr[i] = temp[i];
    
    return inv_count;
}

long long mergeSort(long long arr[],long long temp[],long long left,long long right)
{
    long long mid,inv_count = 0;
    if(right > left)
    {
        mid = (left + right)/2;

        inv_count += mergeSort(arr,temp,left,mid);
        inv_count += mergeSort(arr,temp,mid+1,right);

        inv_count += merge(arr,temp,left,mid+1,right);
    }
    return inv_count;
}
long long int inversionCount(long long arr[], long long n)
{
    long long temp[n];
    long long ans = mergeSort(arr, temp, 0, n-1);
    return ans;
    // Your Code Here
}
```

```
TC:- O(nlogn)
SC:- O(n)
```
