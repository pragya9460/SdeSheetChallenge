# [Find intersection point of Y linkedlist](https://leetcode.com/problems/intersection-of-two-linked-lists/)

### Code || (TBC)

``` .cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if(headA==NULL or headB==NULL){
            return NULL;
        }
        ListNode* a= headA, *b = headB;
        while(a!=b){
            a = a==NULL?headA:a->next;
            b = b==NULL?headB:b->next;
        }
        return a;
    }
};
```
