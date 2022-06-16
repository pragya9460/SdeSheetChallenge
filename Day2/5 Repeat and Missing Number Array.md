# [Repeat and Missing Number Array](https://practice.geeksforgeeks.org/problems/find-missing-and-repeating2512/1/)

### Code || [Notes](https://drive.google.com/file/d/1_jJ3gypu30RaIG4S2gkCApI-D3jGj2_Y/view?usp=sharing)
``` .cpp
class Solution{
public:
    int *findTwoElement(int *arr, int n) {
        
        int *ans = new int(2);
    int xor1;

    int set_bit_no;

    int i;
    int x = 0; // missing
    int y = 0; // repeating
    int n = arr.size();

    xor1 = arr[0];
    for (i = 1; i < n; i++)
        xor1 = xor1 ^ arr[i];

    for (i = 1; i <= n; i++)
        xor1 = xor1 ^ i;

    set_bit_no = xor1 & ~(xor1 - 1);

    for (i = 0; i < n; i++) {
        if (arr[i] & set_bit_no)
            x = x ^ arr[i];

        else
            y = y ^ arr[i];
    }

    for (i = 1; i <= n; i++) {
        if (i & set_bit_no)
            x = x ^ i;

        else
            y = y ^ i;
    }

    
        int xc =0;
        for(int i=0; i<n; i++){
            if(arr[i]==x){
                xc++;
            }
        }
        if(xc==2){
            ans[0]=x, ans[1]=y;
        } 
        else{
            ans[0]=y, ans[1]=x;
        }
        return ans;
     }
};
```

```
TC:- O(n)
SC:- O(1)
```
