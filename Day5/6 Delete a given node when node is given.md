# [Delete a given node when node is given](https://leetcode.com/problems/delete-node-in-a-linked-list/)

### Code || (TBC)

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
