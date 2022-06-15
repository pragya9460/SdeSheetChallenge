# [Remove nth node from back of LinkedList](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

### Code || [Notes](https://drive.google.com/file/d/1P6s6vE_p53GiclOUpzYOi2SfimDVFN_x/view?usp=sharing)
``` .cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* start = new ListNode();
        start->next = head;
        ListNode* fast = start, *slow = start;
        for(int i=1; i<=n; i++){
            fast = fast->next;
        }
        while(fast->next!=NULL){
            fast = fast->next;
            slow = slow->next;
        }
        slow->next = slow->next->next;
        return start->next;
    }   
};
```

```
TC:- O(n)
SC:- O(1)
```
