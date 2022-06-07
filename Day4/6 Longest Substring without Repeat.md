# [Longest Substring without Repeat](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

### Code || [Notes](https://drive.google.com/file/d/1P-ymmh2shly4mOsypwQi03GWN5rrwXFn/view?usp=sharing)
``` .cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char, int> m;
        int right = 0, left=0, n = s.size(), len=0;
        while(right<n){
            if(m.find(s[right])!=m.end()){
                left = max(left, m[s[right]]+1);
            }
            m[s[right]]=right;
            len = max(len, right-left+1);
            right++;
        }
        return len;
    }
};
```
