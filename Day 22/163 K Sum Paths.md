# Approach (Brute Force)
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n<sup>2</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(h)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    int ans=0;
  public:

    void recur(Node*root,int k,int sum){
        if(root==NULL)
            return;
        
        sum+=root->data;
        if(sum==k){
            ans++;
        }
        recur(root->left,k,sum);
        recur(root->right,k,sum);
    }
    void solve(Node*root,int k){
        if(root==NULL)
            return;
        
        recur(root,k,0);
        solve(root->left,k);
        solve(root->right,k);
    }
    int sumK(Node *root, int k) {
        // code here
        solve(root,k);
        return ans;
    }
};
```


# Approach (Using Map)
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(h)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    int ans=0;
  public:
    void solve(Node *root,int k,unordered_map<int,int> &mp,int &ans,int sum){
        if(root==NULL){
            return;
        }
        sum+=root->data;
        if(mp.find(sum-k) != mp.end()){
            ans+=mp[sum-k];
        }
        mp[sum]++;
        
        solve(root->left,k,mp,ans,sum);
        solve(root->right,k,mp,ans,sum);
        
        mp[sum]--;
    }
    int sumK(Node *root,int k)
    {
        // code here 
        int ans=0;
        unordered_map<int,int>mp;
        mp[0]=1;
        solve(root,k,mp,ans,0);
        return ans;
    }
};
```
