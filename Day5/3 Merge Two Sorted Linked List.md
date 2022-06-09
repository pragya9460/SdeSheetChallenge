# [Merge Two Sorted Linked List](https://leetcode.com/problems/merge-two-sorted-lists/)

### Code || (TBC)

``` .cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if(l1==NULL) return l2;
        if(l2==NULL) return l1;
        ListNode* t1=l1, *t2=l2;
        ListNode* dummy = new ListNode(-1);
        ListNode* head = dummy;
        while(t1 and t2){
            if(t1->val>t2->val){
                dummy->next=t2;
                t2=t2->next;
            }
            else{
                dummy->next = t1;
                t1=t1->next;
            }
            dummy=dummy->next;
        }
        if(t1){
            dummy->next = t1;
        }
        if(t2){
            dummy->next = t2;
        }
        return head->next;
    }
};
```
