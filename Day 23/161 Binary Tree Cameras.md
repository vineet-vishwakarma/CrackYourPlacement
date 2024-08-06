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
    int sum=0;
    int dfs(TreeNode*root){
        if(root==NULL)
            return 1;
        
        int left=dfs(root->left);
        int right=dfs(root->right);

        if(left==0 || right==0){
            sum++;
            return 2;
        }else if(left==2 || right==2){
            return 1;
        }else{
            return 0;
        }
    }
    int minCameraCover(TreeNode* root) {
        if(dfs(root)==0)
            sum++;
        
        return sum;
    }
};
```
