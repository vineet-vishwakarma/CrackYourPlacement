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
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if(!list1 && !list2)
            return list1;
        else if(list1==NULL && list2!=NULL)
            return list2;
        else if(list1!=NULL && list2==NULL)
            return list1;

        ListNode*dummyHead=new ListNode(-1);
        ListNode*dummy=dummyHead;

        while(list1 && list2){
            if(list1->val<list2->val){
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
};
```
