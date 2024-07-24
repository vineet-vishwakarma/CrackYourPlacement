# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n) recursive stack
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    ListNode* findMiddle(ListNode* head){
        ListNode*slow=head;
        ListNode*fast=head->next;
        while(fast!=NULL &&fast->next!=NULL){
            slow=slow->next;
            fast= fast->next->next;
        }
        return slow;
    }

    ListNode* merge(ListNode* list1, ListNode* list2) {
        if(!list1 && !list2)
            return list1;
        else if(list1==NULL && list2!=NULL)
            return list2;
        else if(list1!=NULL && list2==NULL)
            return list1;

        ListNode*dummyHead=new ListNode(-1);
        ListNode*dummy=dummyHead;

        while(list1 && list2){
            if(list1->val<=list2->val){
                dummy->next=list1;
                list1=list1->next;
            }else{
                dummy->next=list2;
                list2=list2->next;
            }
            dummy=dummy->next;
        }

        if(list1){
            dummy->next=list1;
        }
        if(list2){
            dummy->next=list2;
        }
        return dummyHead->next;
    }

    ListNode* sortList(ListNode* head) {
        if(!head || !head->next)
            return head;
        
        ListNode*middle=findMiddle(head);
        ListNode*left=head;
        ListNode*right=middle->next;
        middle->next=NULL;

        left=sortList(left);
        right=sortList(right);

        return merge(left,right);
    }
};
```
