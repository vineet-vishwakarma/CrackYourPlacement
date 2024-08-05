 Approach
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
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Codec {
public:

    // Encodes a tree to a single string.
    string serialize(TreeNode* root) {
        if(root==NULL)
            return "";
        
        string s="";
        queue<TreeNode*>q;
        q.push(root);

        while(!q.empty()){
            int n=q.size();
            for(int i=0;i<n;i++){
                auto curr=q.front();
                q.pop();

                if(curr==NULL)
                    s.append("#,");
                else{
                    s.append(to_string(curr->val)+',');
                }
                if(curr!=NULL){
                    q.push(curr->left);
                    q.push(curr->right);
                }
            }
        }
        return s;
    }

    // Decodes your encoded data to tree.
    TreeNode* deserialize(string data) {
        if(data.size()==0)
            return NULL;
        
        stringstream s(data);
        string str;
        getline(s,str,',');

        TreeNode*root=new TreeNode(stoi(str));
        queue<TreeNode*>q;
        q.push(root);
        
        while(!q.empty()){
            auto curr=q.front();
            q.pop();

            getline(s,str,',');
            if(str=="#"){
                curr->left=NULL;
            }else{
                curr->left=new TreeNode(stoi(str));
                q.push(curr->left);
            }

            getline(s,str,',');
            if(str=="#"){
                curr->right=NULL;
            }else{
                curr->right=new TreeNode(stoi(str));
                q.push(curr->right);
            }
        }

        return root;
    }
};

// Your Codec object will be instantiated and called as such:
// Codec ser, deser;
// TreeNode* ans = deser.deserialize(ser.serialize(root));
```
