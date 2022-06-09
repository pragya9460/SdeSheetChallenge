# [Find the middle of Linkedlist](https://leetcode.com/problems/middle-of-the-linked-list/)

### Code || (TBC)
``` .cpp
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode* fast=head, *slow = head;
        while(fast!=NULL and fast->next!=NULL){
            fast = fast->next->next;
            slow = slow->next;
        }
        return slow;
    }
};
```
