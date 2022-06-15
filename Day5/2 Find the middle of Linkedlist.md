# [Find the middle of Linkedlist](https://leetcode.com/problems/middle-of-the-linked-list/)

### Code || [Notes](https://drive.google.com/file/d/1PTdY_EvqgXsJ1SYQy6-d2hFKqoCwCBjZ/view?usp=sharing)
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

```
TC:- O(n)
SC:- O(1)
```
