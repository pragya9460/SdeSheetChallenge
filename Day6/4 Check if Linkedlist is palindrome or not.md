# [Check if Linkedlist is palindrome or not](https://leetcode.com/problems/palindrome-linked-list/)

### Code || [Notes](https://drive.google.com/file/d/11JBH_JKoWqxNE3A1NrOk7ofLfJuYeiFF/view?usp=sharing)

``` .cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* newhead = NULL;
        while(head!=NULL){
            ListNode* next = head->next;
            head->next = newhead;
            newhead = head;
            head = next;
        }
        return newhead;
    }
    bool isPalindrome(ListNode* head) {
        if(head==NULL or head->next==NULL)  return true;
        
        ListNode* slow = head, *fast = head;
        while(fast->next!=NULL and fast->next->next!=NULL){
            slow = slow->next;
            fast = fast->next->next;
        }
        slow->next = reverseList(slow->next);
        slow = slow->next;
        while(slow!=NULL){
            if(head->val!=slow->val){
                return false;
            }
            slow = slow->next;
            head = head->next;
        }
        return true;
    }
};
```

```
TC:- O(n)
SC:- O(1)
```
