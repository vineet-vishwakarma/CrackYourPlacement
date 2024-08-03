# Code
```
class Solution{
public:
    int count=0;
    void recur(Node*root,int l,int h){
        if(root==NULL)
            return;
        
        recur(root->left,l,h);
        if(root->data>=l && root->data<=h){
            count++;
        }
        recur(root->right,l,h);
    }
    int getCount(Node *root, int l, int h)
    {
        // your code goes here  
        recur(root,l,h);
        return count;
    }
};
```
