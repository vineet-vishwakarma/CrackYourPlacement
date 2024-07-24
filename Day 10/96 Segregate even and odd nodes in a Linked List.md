# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution{
public:
    Node* divide(int N, Node *head){
        // code here
        if(head==NULL) 
            return head;
        
        Node*evenHead=new Node(-1);
        Node*oddHead=new Node(-1);
        
        Node*even=evenHead;
        Node*odd=oddHead;
        
        while(head){
            if(head->data%2==0){
                even->next=head;
                even=even->next;
            }else{
                odd->next=head;
                odd=odd->next;
            }
            head=head->next;
        }
        odd->next = NULL;
        even->next = oddHead->next;
        
        return evenHead->next;
    }
};
```
