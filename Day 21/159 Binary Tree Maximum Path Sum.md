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
    int sum=INT_MIN;
    int maxSum(TreeNode*root){
        if(root==NULL)
            return 0;
        
        int left=max(maxSum(root->left),0);
        int right=max(maxSum(root->right),0);
        int currSum=root->val+left+right;
        sum=max(currSum,sum);
        return root->val+max(left,right);
    }
    int maxPathSum(TreeNode* root) {
        maxSum(root);
        return sum;
    }
};
```
