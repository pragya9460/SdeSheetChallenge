# [Reverse Linkedlist in group of size k](https://leetcode.com/problems/reverse-nodes-in-k-group/)

### Code || [Notes](https://drive.google.com/file/d/1ewXciFlalfeBIlAAMm706dkS4lFzsdmr/view?usp=sharing)

```.cpp
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        if(head==NULL or k==1){
            return head;
        }
        ListNode* dummy = new ListNode(0);
        dummy->next = head;
        ListNode* cur = dummy, *nex = dummy, *pre = dummy;
        int count=0;
        while(cur->next!=NULL){
            cur = cur->next;
            count++;
        }
        while(count>=k){
            cur = pre->next;
            nex = cur->next;
            for(int i=1; i<k; i++){
                cur->next = nex->next;
                nex->next = pre->next;
                pre->next = nex;
                nex = cur->next;
            }
            pre = cur;
            count-=k;
        }
        return dummy->next;
    }
};
```

```
TC:- O(n)
SC:- O(1)
```
