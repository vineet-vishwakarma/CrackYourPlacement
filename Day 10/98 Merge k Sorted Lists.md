# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogm)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n) recursive stack
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
    ListNode* merge(ListNode* l1, ListNode* l2){
        ListNode*dummyHead=new ListNode(-1);
        ListNode*dummy=dummyHead;
        
        while(l1 && l2){
            if(l1->val<l2->val){
                dummy->next=l1;
                l1=l1->next;
            }else{
                dummy->next=l2;
                l2=l2->next;
            }
            dummy=dummy->next;
        }
        
        dummy->next=l1 ? l1 : l2;
        
        return dummyHead->next;
    }

    ListNode* mergeK(vector<ListNode*>& lists, int start, int end) {
        if(start==end){
            return lists[start];
        }
        
        if(start+1==end){
            return merge(lists[start],lists[end]);
        }
        
        int mid=start+(end-start)/2;
        
        ListNode*left=mergeK(lists,start,mid);
        ListNode*right=mergeK(lists,mid+1,end);
        
        return merge(left,right);
    }
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        if(lists.empty()){
            return nullptr;
        }
        return mergeK(lists,0,lists.size()-1);
    }
};
```
