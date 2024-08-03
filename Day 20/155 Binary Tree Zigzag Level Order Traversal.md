# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
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
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        if(root==NULL)
            return {};

        vector<vector<int>>ans;
        bool dir=true;

        queue<TreeNode*>q;
        q.push(root);

        while(!q.empty()){
            int s=q.size();
            vector<int>v;
            
            for(int i=0;i<s;i++){
                auto curr=q.front();
                q.pop();
                v.push_back(curr->val);

                if(curr->left)
                    q.push(curr->left);
                if(curr->right)
                    q.push(curr->right);
            }
            if(dir==false){
                reverse(v.begin(),v.end());
            }
            ans.push_back(v);
            dir=!dir;
        }
        return ans;
    }
};
```
