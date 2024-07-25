# Approach
- Calulate the size of LL
- if size < k, return head
- reverse upto k
- if more element is present then reverse them recursively
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
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
    ListNode* reverseKGroup(ListNode* head, int k) {
        if(head==NULL)
            return head;
        
        int i=0;
        ListNode*temp=head;
        while(temp){
            temp=temp->next;
            i++;
        }
        if(i<k)
            return head;
        
        int count=0;
        ListNode*forward=NULL;
        ListNode*curr=head;
        ListNode*prev=NULL;

        while(curr && count<k){
            forward=curr->next;
            curr->next=prev;
            prev=curr;
            curr=forward;
            count++;
        }

        if(forward)
            head->next=reverseKGroup(forward,k);

        return prev;
    }
};
```
