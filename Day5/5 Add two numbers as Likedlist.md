# [Add two numbers as Likedlist](https://leetcode.com/problems/add-two-numbers/)

### Code || [Notes](https://drive.google.com/file/d/1P7mVNcGfKjAM-ZRuF04Dnmi6qH1_3I9O/view?usp=sharing)

``` .cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dummy = new ListNode(0);
        ListNode* temp = dummy;
        int carry = 0;
        while(l1!=NULL or l2!=NULL ){
            int sum = 0;
            if(l1!=NULL){
                sum+= l1->val;
                l1 = l1->next;
            }
            if(l2!=NULL){
                sum+= l2->val;
                l2 = l2->next;
            }
            sum+=carry;
            carry = sum/10;
            int n = sum%10;
            temp->next = new ListNode(n);
            temp = temp->next;
        }
        if(carry>0){
            temp->next = new ListNode(carry);
        }
        return dummy->next;
    }
};
```

```
TC:- O(max(m, n))
SC:- O(N)   where, (N = m+n)
```
