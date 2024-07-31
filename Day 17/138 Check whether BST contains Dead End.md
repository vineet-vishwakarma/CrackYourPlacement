# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: (n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution{
  public:
    set<int>s{0};
    
    bool dfs(Node *root)
    {
        //Your code here
        if(root==NULL)
            return false;
        
        if(root->left==NULL && root->right==NULL){
            if(s.find(root->data-1)!=s.end() && s.find(root->data+1)!=s.end()){
                return true;
            }
        }
        s.insert(root->data);
        
        return dfs(root->left) || dfs(root->right);
    }
    bool isDeadEnd(Node*root){
        return dfs(root);
    }
};
```
