# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(height)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(height)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution
{
    public:
    void pres(Node*root,Node*&pre,int key){
        if(root==NULL)
            return;
        
        pres(root->left,pre,key);
        if(root->key<key){
            pre=root;
        }
        pres(root->right,pre,key);
    }
    void sucs(Node*root,Node*&suc,int key){
        if(root==NULL)
            return;
        
        sucs(root->right,suc,key);
        if(root->key>key){
            suc=root;
        }
        sucs(root->left,suc,key);
    }
    void findPreSuc(Node* root, Node*& pre, Node*& suc, int key)
    {
        // Your code goes here
        pres(root,pre,key);
        sucs(root,suc,key);
    }
};
```
