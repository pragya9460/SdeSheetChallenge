# [Delete a given node when node is given](https://leetcode.com/problems/delete-node-in-a-linked-list/)

### Code || [Notes](https://drive.google.com/file/d/1PEWCBIF1WEoDU_aSecnEXV-EsPM2j8Pe/view?usp=sharing)

``` .cpp
class Solution {
public:
    void deleteNode(ListNode* node) {
        node->val = node->next->val;
        node->next = node->next->next;
        return;
    }
};
```

```
TC:- O(1)
SC:- O(1)
```
