 Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
Node *build(int &i, int n, int pre[], char preLN[])
{
    if(i>=n)
        return NULL;
    
    Node*root= new Node(pre[i]);
    
    if(preLN[i]=='L')
        return root;
    
    i=i+1;
    root->left=build(i,n,pre,preLN);
    i=i+1;
    root->right=build(i,n,pre,preLN);
    
    return root ;
}
struct Node *constructTree(int n, int pre[], char preLN[])
{
    int i=0;
    Node *root= build(i,n,pre,preLN);
    return root ;
}
```
