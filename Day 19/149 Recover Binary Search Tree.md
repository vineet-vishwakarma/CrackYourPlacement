# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n) recursive stack
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
    TreeNode*prev;
    TreeNode*first;
    TreeNode*second;
    void inorder(TreeNode*root){
        if(root==NULL)
            return;
        
        inorder(root->left);
        if(prev && root->val<prev->val){
            if(!first){
                first=prev;
            }
            second=root;
        }
        prev=root;
        inorder(root->right);
    }
public:
    void recoverTree(TreeNode* root) {
        prev=first=second=NULL;
        
        inorder(root);

        if(first && second){
            swap(first->val,second->val);
        }
    }
};
```
