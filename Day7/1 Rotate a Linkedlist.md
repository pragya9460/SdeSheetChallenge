# [Rotate a Linkedlist](https://leetcode.com/problems/rotate-list/description/)

### Code || 

``` .cpp
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if(head==NULL or head->next==NULL or k==0){
            return head;
        }
        ListNode* temp = head;
        int len = 1;
        while(temp->next!=NULL){
            temp= temp->next;
            len++;
        }
        temp->next = head;
        k = k%len;
        k = len-k;
        while(k--){
            temp = temp->next;
        }
        head = temp->next;
        temp->next = NULL;
        return head;
    }
};
```
