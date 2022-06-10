# [Find the starting point of loop in Linkedlist](https://leetcode.com/problems/linked-list-cycle-ii/)

### Code || (TBC)

``` .cpp
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode *fast = head;
        ListNode *slow = head;
        while(fast !=NULL && fast->next!=NULL){
            slow=slow->next;
            fast=fast->next->next;
            if(fast==slow){
                break;
            }
        }
        if(fast==NULL || fast->next==NULL){
            return NULL;
        }
        slow=head;
        while(slow!=fast){
            slow=slow->next;
            fast=fast->next;
        }
        return fast;
    }
};
```
