# Approach
- Remove leading zeros
- Find the length of LL
- Identify the greater number
- Reverse both LLs
- Actual Subtraction
- Subtraction on remaining part
- Reverse the LL
- Remove leading zeros 
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
    Node*removeLeadingZeroes(Node*head){
        
        while(head && head->next && head->data==0){
            Node*trash=head;
            head=head->next;
        }
        
        return head;
    }

    int len(Node*head){
        Node*temp=head;
        int count=0;
        
        while(temp){
           temp=temp->next;
           count++;
        }
        
        return count;
    }
    
    Node*reverse(Node*head){
        Node*prev=NULL;
        Node*curr=head;
        Node*forward=NULL;
        
        while(curr){
           forward=curr->next;
           curr->next=prev;
           prev=curr;
           curr=forward;
        }
        
        return prev;
    }
    
    Node* subLinkedList(Node* head1, Node* head2) {
        // Your implementation of subLinkedList goes here
        // Make sure to return the head of the resulting linked list
        head1=removeLeadingZeroes(head1);
        head2=removeLeadingZeroes(head2);
        
        int l1=len(head1);
        int l2=len(head2);
        
        if(l2>l1){
            swap(head1,head2);
        } 
        
        if(l1 == l2){
            Node*c1=head1;
            Node*c2=head2;
            
            while(c1 && c2){
                if(c1->data > c2->data) 
                    break;
                
                if(c1->data < c2->data){
                    swap(head1, head2);
                    break;
                }
                
                c1=c1->next;
                c2=c2->next;
            }
        }
        
        int carry=0;
        head1=reverse(head1);
        head2=reverse(head2);
        
        Node*curr1=head1;
        Node*curr2=head2;
        
        while(curr1 && curr2){
            
            int a=curr1->data;
            int b=curr2->data;
        
            if((a+carry)<b){
                curr1->data=a+10+carry-b;
                if(!carry)
                    carry=-1;
            }else{
                curr1->data=a+carry-b;
                carry=0;
            }
            
            curr1=curr1->next;
            curr2=curr2->next;
        }
        
        while(carry && curr1){
            
            int a=curr1->data;
            if((carry + a)<0){
                a+=10+carry;
            }else{
                a+=carry;
                carry=0;
            }
            curr1->data=a;
            curr1=curr1->next;
        }

        return removeLeadingZeroes(reverse(head1));
    }
};
```
