# [Aggressive Cows](https://www.spoj.com/problems/AGGRCOW/)

### Code

``` .cpp
#include <bits/stdc++.h>
using namespace std;

bool isPossible(vector<int> &a, int n, int cows, int minDist) {
      int cntCows = 1;
      int lastPlacedCow = a[0];
      for (int i = 1; i < n; i++) {
        if (a[i] - lastPlacedCow >= minDist) {
          cntCows++;
          lastPlacedCow = a[i];
        }
      }
      if (cntCows >= cows) return true;
      return false;
    }

int main() {
	int t;
	cin>>t;
	while(t--){
		int n, c;
		cin>>n>>c;
		vector<int> a(n);
		for(int i=0; i<n; i++){
			cin>>a[i];
		}
		sort(a.begin(), a.end());
		int low = 1, high = a[n - 1] - a[0];

	      while (low <= high) {
	        int mid = (low + high) >> 1;
	
	        if (isPossible(a, n, c, mid)) {
	          low = mid + 1;
	        } else {
	          high = mid - 1;
	        }
	      }
	      cout<<high<<endl;
	}
	return 0;
}
```

```
TC:- O(nlogn)
SC:- O(1)
```
