# [Detect a cycle in a Linkedlist](https://leetcode.com/problems/linked-list-cycle/)

### Code || (TBC)

``` .cpp
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if(head==NULL or head->next==NULL){
            return false;
        }
        ListNode* fast=head, *slow=head;
        while(fast and fast->next){
            fast=fast->next->next;
            slow=slow->next;
            if(fast==slow){
                return true;
            }
        }
        return false;
    }
};
```
