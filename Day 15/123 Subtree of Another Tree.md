# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
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
    bool isIdentical(TreeNode*root,TreeNode* subRoot){
        if(root==NULL && subRoot==NULL){
            return true;
        }
        
        if((root==NULL && subRoot!=NULL) || (root!=NULL && subRoot==NULL)){
            return false;
        }
        
        if(root->val!=subRoot->val){
            return false;
        }else{
            return(isIdentical(root->left,subRoot->left) && isIdentical(root->right,subRoot->right));
        }

    }

    bool isSubtree(TreeNode* root, TreeNode* subRoot) {
        if(!root)
            return false;
        
        else if(isIdentical(root,subRoot)){
            return true;
        }else{
            return isSubtree(root->left,subRoot)||isSubtree(root->right,subRoot);
        }
    }
};
```
