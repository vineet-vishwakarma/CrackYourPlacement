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
    ListNode* deleteDuplicates(ListNode* head) {
        if(!head || !head->next)
            return head;
        
        ListNode*dummyHead=new ListNode(-1);
        dummyHead->next=head;
        ListNode*dummy=dummyHead;

        while(head){
            if(head->next && head->val==head->next->val){
                while(head->next && head->val==head->next->val){
                    head=head->next;
                }
                dummy->next=head->next;
            }else{
                dummy=dummy->next;
            }
            head=head->next;
        }
        return dummyHead->next;
    }
};
```