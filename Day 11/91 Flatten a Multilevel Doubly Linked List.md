# Approach
- If curr->child save forward=curr->next
- Flatten the DLL recursively
- Iterate the flatten DLL until flat->next
- Make connection with forward
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(N)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* prev;
    Node* next;
    Node* child;
};
*/

class Solution {
public:
    Node* flatten(Node* head) {
        if(head==NULL)
            return head;
        
        Node*curr=head;

        while(curr){
            Node*forward=curr->next;
            if(curr->child){
                Node*flat=flatten(curr->child);
                curr->next=flat;
                flat->prev=curr;
                while(flat->next){
                    flat=flat->next;
                }
                flat->next=forward;
                if(forward)
                    forward->prev=flat;
                flat->child=NULL;
                curr->child=NULL;
            }
            curr=curr->next;
        }

        return head;
    }
};
```
