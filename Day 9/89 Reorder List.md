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
    ListNode*reverse(ListNode*head){
        if(head==NULL)
            return head;
        
        ListNode*prev=NULL;
        ListNode*curr=head;
        ListNode*forward=NULL;

        while(curr){
            forward=curr->next;
            curr->next=prev;
            prev=curr;
            curr=forward;
        }
        return prev;
    }
    void reorderList(ListNode* head) {
        if(!head || !head->next || !head->next->next)
            return;

        ListNode*slow=head;
        ListNode*fast=head;

        while(fast && fast->next){
            slow=slow->next;
            fast=fast->next->next;
        }

        ListNode*L2=reverse(slow->next);
        slow->next=NULL;
        ListNode*L1=head;

        while(L1 && L2){
            ListNode*t1=L1->next;
            ListNode*t2=L2->next;
            
            L1->next=L2;
            L2->next=t1;

            L1=t1;
            L2=t2;
        }
    }
};
```
