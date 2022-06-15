# [Reverse a Linkedlist](https://leetcode.com/problems/reverse-linked-list/)

### Code || [Notes](https://drive.google.com/file/d/1PSmdcgoXevDJGxgWavgH4rq2JcEhsEYf/view?usp=sharing)

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
};
```

```
TC:- O(n)
SC:- O(1)
```
