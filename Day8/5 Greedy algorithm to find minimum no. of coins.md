# [Greedy algorithm to find minimum no. of coins](https://www.geeksforgeeks.org/find-minimum-number-of-coins-that-make-a-change/)

### Code ||

``` .cpp
void findmin(int v){
  int deno[]={1, 2, 5, 10, 20, 50, 100, 500, 1000};
  int n = 9;
  vector<int> ans;
  for(int i=n-1; i>=0; i--){
      while(v>=deno[i]){
          v-=deno[i];
          ans.push_back(deno[i]);
      }
  }
  cout<<ans.size()<<endl;
}
```

```
TC:- O(v)
SC:- O(1)
```
