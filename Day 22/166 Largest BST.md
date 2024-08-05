 Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(h)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution{
    public:
    /*You are required to complete this method */
    // Return the size of the largest sub-tree which is also a BST
    vector<int>solve(Node*root){
        if(root==NULL){
            return {0,1,INT_MAX,INT_MIN};
        }
        
        if(root->left==NULL && root->right==NULL){
            return {1,1,root->data,root->data};
        }
        
        vector<int>left=solve(root->left);
        vector<int>right=solve(root->right);
        
        if(left[1]==1 && right[1]==1 
        && root->data > left[3] 
        && root->data < right[2]){
            return {left[0]+right[0]+1,1,min(root->data,left[2]),max(root->data,right[3])};
        }else{
            return {max(left[0],right[0]),0,0,0};
        }
    }
    int largestBst(Node *root)
    {
    	//Your code here
    	return solve(root)[0];
    }
};
```
