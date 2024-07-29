# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
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
    bool recur(TreeNode*r1,TreeNode*r2)
    {
        if(r1==NULL && r2==NULL)
            return true;

        if(r1==NULL || r2==NULL)
            return false;
            
        if(r1->val!=r2->val)
            return false;

        return (recur(r1->left,r2->right) && recur(r1->right,r2->left));
    }
    bool isSymmetric(TreeNode* root) {
        if(recur(root->left,root->right))
            return true;
        else return false;
    }
};
```
