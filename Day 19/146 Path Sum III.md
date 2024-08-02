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
    void pre(TreeNode* root, int targetSum,long long sum,int&count){
        if(root==NULL)
            return;
        
        sum+=root->val;
        if(sum==targetSum){
            count++;
        }
        pre(root->left,targetSum,sum,count);
        pre(root->right,targetSum,sum,count);
    }
    void dfs(TreeNode* root, int targetSum,long long sum,int&count){
        if(root==NULL)
            return;
        pre(root,targetSum,sum,count);
        dfs(root->left,targetSum,sum,count);
        dfs(root->right,targetSum,sum,count);
    }
    int pathSum(TreeNode* root, int targetSum) {
        long long sum=0;
        int count=0;
        dfs(root,targetSum,sum,count);
        return count;
    }
};
```
