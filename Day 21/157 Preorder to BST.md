# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public:
    // Function that constructs BST from its preorder traversal.
    Node* Bst(int pre[], int size) {
        // code here
        Node*root=newNode(pre[0]);
        Node*curr;
        
        for(int i=1;i<size;i++){
            curr=root;
            while(curr!=NULL){
                if(pre[i]<curr->data){
                    if(curr->left)
                        curr=curr->left;
                    else {   
                        curr->left=newNode(pre[i]);
                        break;
                    }
                }
                else{
                    if(curr->right)
                        curr=curr->right;
                    else {   
                        curr->right=newNode(pre[i]);
                        break;
                    }
                }
            }
        }
        return root;
    }
};
```
