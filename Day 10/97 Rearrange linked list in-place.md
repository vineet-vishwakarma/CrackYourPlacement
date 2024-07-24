# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public:
    Node*reverseLL(Node*head)
    {
        Node*prev=NULL;
        Node*forward=NULL;
        Node*curr=head;
            
        while(curr!=NULL)
        {
            forward=curr->next;
            curr->next=prev;
            prev=curr;
            curr=forward;
        }
        return prev;
    }
    
    Node *inPlace(Node *head)
    {
        // your code goes here
        if(head==NULL && head->next==NULL)
                return head;
            
            Node*slow=head;
            Node*fast=head->next;
            
            while(fast!=NULL&&fast->next!=NULL)
            {
                slow=slow->next;
                fast=fast->next->next;
            }
            Node*reverse=slow->next;
            slow->next=NULL;
            reverse=reverseLL(reverse);
            
            Node*temp=head;
            while(reverse!=NULL&&temp!=NULL)
            {
                Node*tempNext=temp->next;
                temp->next=reverse;
                temp=tempNext;
                Node*reverseNext=reverse->next;
                reverse->next=temp;
                reverse=reverseNext;
            }
            return head;
    }
};
```
