# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
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
    void recur(TreeNode*root,map<int,vector<pair<int,int>>>& mp,int x,int y){
        if(root==NULL)
            return;
        recur(root->left,mp,x-1,y-1);
        
        mp[x].push_back({y,root->val});
        sort(mp[x].begin(),mp[x].end(), [](pair<int,int>p1,pair<int,int>p2){
            if(p1.first==p2.first){
                return p1.second<p2.second;
            }
            return p1.first>p2.first;
        });

        recur(root->right,mp,x+1,y-1);
    }
    vector<vector<int>> verticalTraversal(TreeNode* root) {
        map<int,vector<pair<int,int>>>mp;
        vector<vector<int>>ans;
        recur(root,mp,0,0);

        for(auto i:mp){
            vector<int>temp;
            for(auto j:i.second){
                temp.push_back(j.second);
            }
            ans.push_back(temp);
        }
        return ans;
    }
};
```
