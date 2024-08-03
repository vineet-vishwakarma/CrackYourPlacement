# Approach
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
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        int s1=0,s2=0;
        ListNode*l1=headA;
        ListNode*l2=headB;

        while(l1){
            s1++;
            l1=l1->next;
        }
        while(l2){
            s2++;
            l2=l2->next;
        }
        l1=headA;
        l2=headB;
        
        int diff=abs(s1-s2);
        if(s1>s2){
            while(diff--){
                l1=l1->next;
            }
        }else{
            while(diff--){
                l2=l2->next;
            }
        }

        while(l1 && l2){
            if(l1==l2)
                return l1;
            
            l1=l1->next;
            l2=l2->next;
        }

        return NULL;
    }
};
```
