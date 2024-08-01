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
    bool recur(TreeNode*root,TreeNode* maxi,TreeNode* mini){
        if(root==NULL)
            return true;
        
        if(maxi && root->val>=maxi->val){
            return false;
        }
        if(mini && root->val<=mini->val){
            return false;
        }
        
        return recur(root->left,root,mini) && recur(root->right,maxi,root);
    }
    bool isValidBST(TreeNode* root) {
        return recur(root,NULL,NULL);
    }
};
```
