# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n+m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode*head=new ListNode(0);
        ListNode*temp=head;
        
        int carry=0;

        while(l1!=NULL || l2!=NULL || carry!=0){
            int digit1 = l1==NULL?0:l1->val;
            int digit2 = l2==NULL?0:l2->val;

            int sum=digit1+digit2+carry;
            int num=sum%10;
            carry=sum/10;

            temp->next=new ListNode(num);
            temp=temp->next;

            l1=l1!=NULL?l1->next:NULL;
            l2=l2!=NULL?l2->next:NULL;
        }

        return head->next;
    }
};
```