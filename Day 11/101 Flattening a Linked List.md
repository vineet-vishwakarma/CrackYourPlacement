# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m) recursive stack
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
Node* merge(Node* l1, Node* l2)
{
    if(l1==NULL)
        return l2;
        
    if(l2==NULL)
        return l1;

    Node*dummyHead=new Node(-1);
    Node*dummy=dummyHead;

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

    if(l1){
        dummy->next=l1;
    }
    if(l2){
        dummy->next=l2;
    }
    return dummyHead->next;
}
 
Node* flatten(Node* root)
{
    if (root == NULL || root->next == NULL)
        return root;

    root->next = flatten(root->next);

    root = merge(root, root->next);
    
    return root;
}
```
