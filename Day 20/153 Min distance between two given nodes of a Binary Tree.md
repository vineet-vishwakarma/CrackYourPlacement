# Complexity
- Time Complexity: O(n)
- Space Complexity: O(h)

# Code
```
class Solution{
    public:
    /* Should return minimum distance between a and b
    in a tree with given root*/
    Node*lca(Node*root,int a,int b){
        if(root==NULL || root->data==a || root->data==b)
            return root;
        
        Node*left=lca(root->left,a,b);
        Node*right=lca(root->right,a,b);
        
        if(left && right){
            return root;
        }else if(left){
            return left;
        }else{
            return right;
        }
    }
    
    int distance(Node*root,int val, int len){
        if(root==NULL)
            return -1;
        
        if(root->data==val){
            return len;
        }
        
        int left=distance(root->left,val,len+1);
        
        if(left!=-1){
            return left;
        }
        
        int right=distance(root->right,val,len+1);
        
        return right;
    }
    int findDist(Node* root, int a, int b) {
        // Your code here
        Node*LCA=lca(root,a,b);
        
        return distance(LCA,a,0)+distance(LCA,b,0);
    }
};
```
