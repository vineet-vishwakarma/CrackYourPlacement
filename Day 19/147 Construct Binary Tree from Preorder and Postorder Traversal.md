# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n<sup>2</sup>)
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
    int findPosition(vector<int>&postorder,int val){
        for(int i=0;i<postorder.size();i++){
            if(postorder[i]==val)
                return i;
        }
        return -1;
    }
    TreeNode*build(vector<int>&preorder,vector<int>&postorder,int&preS,int postS,int postE){
        if(postS>postE)
            return NULL;
        
        TreeNode*root=new TreeNode(preorder[preS]);
        preS++;

        if(postS==postE)
            return root;
        
        int pos=findPosition(postorder,preorder[preS]);

        root->left=build(preorder,postorder,preS,postS,pos);
        root->right=build(preorder,postorder,preS,pos+1,postE-1);

        return root;
    }
    TreeNode* constructFromPrePost(vector<int>& preorder, vector<int>& postorder) {
        int preS=0;
        int postS=0;
        int postE=postorder.size()-1;
        return build(preorder,postorder,preS,postS,postE);
    }
};
```
