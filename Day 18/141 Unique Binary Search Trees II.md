# Complexity
- Time complexity: O(4<sup>n</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(4<sup>n</sup>)
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
    vector<TreeNode*>recur(int left,int right){
        if(left==right){
            return {new TreeNode(left)};
        }
        if(left>right){
            return {NULL};
        }

        vector<TreeNode*>res;
        for(int i=left;i<=right;i++){
            vector<TreeNode*>leftTree=recur(left,i-1);
            for(auto j:leftTree){
                vector<TreeNode*>rightTree=recur(i+1,right);
                for(auto k:rightTree){
                    TreeNode*root=new TreeNode(i,j,k);
                    res.push_back(root);
                }
            }
        }
        return res;
    }
    vector<TreeNode*> generateTrees(int n) {
        return recur(1,n);
    }
};
```
