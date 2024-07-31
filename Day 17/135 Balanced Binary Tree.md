# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(h)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool ans;
    int height(TreeNode*root){
        if(root==NULL)
            return 0;
        
        if(ans==false)
            return 0;
        
        int left=height(root->left);
        int right=height(root->right);

        if(abs(left-right)>1){
            ans=false;
        }
        return 1+max(left,right);
    }
    bool isBalanced(TreeNode* root) {
        ans=true;
        height(root);
        return ans;
    }
};
```
