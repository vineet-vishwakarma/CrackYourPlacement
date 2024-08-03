# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution
{
    public:
    //Function to sort a linked list of 0s, 1s and 2s.
    Node* segregate(Node *head) {
        // Add code here
        if(!head || !head->next)
            return head;
        
        Node*zeroHead=new Node(-1);
        Node*oneHead=new Node(-1);
        Node*twoHead=new Node(-1);
        
        Node*zero=zeroHead;
        Node*one=oneHead;
        Node*two=twoHead;
        
        while(head){
            if(head->data==0){
                zero->next=head;
                zero=zero->next;
            }else if(head->data==1){
                one->next=head;
                one=one->next;
            }else{
                two->next=head;
                two=two->next;
            }
            head=head->next;
        }
        
        zero->next=(oneHead->next)?(oneHead->next):(twoHead->next);
        one->next=twoHead->next;
        two->next=NULL;
        
        return zeroHead->next;
    }
};
```
