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
    Node* zigZag(Node* head) {
        // your code goes here
        Node*temp=head;
        bool flag=true;
        
        while(temp->next){
            if((flag && temp->data>temp->next->data)||(!flag && temp->data<temp->next->data))
                swap(temp->data,temp->next->data);
            
            flag=!flag;
            temp=temp->next;
        }
        return head;
    }
};
```
