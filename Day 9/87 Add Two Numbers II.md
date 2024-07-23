# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(max(n,m))
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode*reverseLL(ListNode*head){
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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode*h1=reverseLL(l1);
        ListNode*h2=reverseLL(l2);

        ListNode*head=new ListNode(-1);
        ListNode*temp=head;

        int carry=0;
        while(h1!=NULL || h2!=NULL || carry!=0){
            int d1= h1==NULL?0:h1->val;
            int d2= h2==NULL?0:h2->val;

            int sum=carry+d1+d2;
            int digit=sum%10;
            carry=sum/10;

            temp->next=new ListNode(digit);
            temp=temp->next;

            h1=h1==NULL? NULL :h1->next;
            h2=h2==NULL? NULL :h2->next;
        }

        return reverseLL(head->next);
    }
};
```
