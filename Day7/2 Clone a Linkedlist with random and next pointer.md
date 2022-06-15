# [Clone a Linkedlist with random and next pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)

### Code ||

``` .cpp
class Solution {
public:
    Node* copyRandomList(Node* head) {
//         step-> 1
        Node* iter = head, *front = head;
        while(iter!=NULL){
            front = iter->next;
            iter->next= new Node(iter->val);
            iter->next->next=front;
            iter = iter->next->next;
        }
        
//         step-> 2
        iter=head;
        while(iter!=NULL){
            if(iter->random!=NULL){
                iter->next->random = iter->random->next;   
            }
            iter = iter->next->next;
        }
        
//         step-> 3
        iter = head;
        Node* dummy = new Node(0);
        Node* copy=dummy;
        while(iter!=NULL){
            front = iter->next->next;
            copy->next = iter->next;
            iter->next = front;
            copy = copy->next;
            iter = iter->next;
        }
        return dummy->next;
    }
};
```
