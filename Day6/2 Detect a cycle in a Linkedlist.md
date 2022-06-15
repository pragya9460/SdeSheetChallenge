# [Detect a cycle in a Linkedlist](https://leetcode.com/problems/linked-list-cycle/)

### Code || [Notes](https://drive.google.com/file/d/1K81dPr10I5cM8KXHrojKW_YBg6U5w07O/view?usp=sharing)

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

```
TC:- O(n)
SC:- O(1)
```
