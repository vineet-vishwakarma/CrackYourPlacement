# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(h)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution
{
    public: 
    //Function to convert binary tree to doubly linked list and return it.
    Node*head=NULL;
    Node*prev=NULL;
    void recur(Node*root){
        if(root==NULL)
            return;
        
        recur(root->left);
        
        if(prev==NULL){
            head=root;
        }else{
            root->left=prev;
            prev->right=root;
        }
        prev=root;
        
        recur(root->right);
    }
    Node*bToDLL(Node *root)
    {
        // your code here
        recur(root);
        return head;
    }
};
```