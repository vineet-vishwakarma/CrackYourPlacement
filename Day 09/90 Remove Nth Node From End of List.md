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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        int size=0;
        ListNode*temp=head;
        while(temp){
            size++;
            temp=temp->next;
        }
        if(size-n==0)
            return head->next;

        int i=0;
        temp=head;
        while(i<size-n-1){
            temp=temp->next;
            i++;
        }
        temp->next=temp->next->next;
        return head;
    }
};
```
