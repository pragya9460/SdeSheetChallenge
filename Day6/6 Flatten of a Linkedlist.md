# [Flatten of a Linkedlist](https://practice.geeksforgeeks.org/problems/flattening-a-linked-list/1)

### Code || [Notes](https://drive.google.com/file/d/11S-ETKZM7gE3syglyJTJ5C5ygj8FBbc4/view?usp=sharing)

``` .cpp
Node* merge(Node* l1, Node* l2) {
        if(l1==NULL) return l2;
        if(l2==NULL) return l1;
        Node* t1=l1, *t2=l2;
        Node* dummy = new Node(-1);
        Node* head = dummy;
        while(t1 and t2){
            if(t1->data>t2->data){
                dummy->bottom=t2;
                t2=t2->bottom;
            }
            else{
                dummy->bottom = t1;
                t1=t1->bottom;
            }
            dummy=dummy->bottom;
        }
        if(t1){
            dummy->bottom = t1;
        }
        if(t2){
            dummy->bottom = t2;
        }
        return head->bottom;
    }

Node *flatten(Node *root)
{
   if(root==NULL or root->next==NULL){
       return root;
   }
   root->next = flatten(root->next);
   root = merge(root, root->next);
   return root;
}
```

```
TC:- O(Total no. of nodes in main branch)
SC:- O(1)
```
