# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int widthOfBinaryTree(TreeNode* root) {
        if(root==NULL)
            return 0;
        
        int ans=0;
        queue<pair<TreeNode*,int>>q;
        q.push({root,0});

        while(!q.empty()){
            int s=q.size();
            int mini=q.front().second;
            int first,last;

            for(int i=0;i<s;i++){
                long long int currInd=q.front().second-mini;
                TreeNode*curr=q.front().first;
                q.pop();

                if(i==0)
                    first=currInd;
                if(i==s-1)
                    last=currInd;
                
                if(curr->left)
                    q.push({curr->left,currInd*2+1});
                if(curr->right)
                    q.push({curr->right,currInd*2+2});
            }
            ans=max(ans,last-first+1);
        }
        return ans;
    }
};
```
