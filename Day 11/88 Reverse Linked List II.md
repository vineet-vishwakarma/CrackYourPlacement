# Approach
- Save left node
- Reverse until the right
- Make right connection 
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
    ListNode* reverseBetween(ListNode* head, int left, int right) {
        if(left==right) 
            return head;
        
        ListNode*dummyHead=new ListNode(-1,head);
        ListNode*curr=head;
        ListNode*leftPrev=dummyHead;

        for(int i=1;i<left;i++){
            curr=curr->next;
            leftPrev=leftPrev->next;
        }

        ListNode*prev=NULL;
        for(int i=0;i<right-left+1;i++){
            ListNode*forward=curr->next;
            curr->next=prev;
            prev=curr;
            curr=forward;
        }
        leftPrev->next->next=curr;
        leftPrev->next=prev;
        
        return dummyHead->next;
    }
};
```