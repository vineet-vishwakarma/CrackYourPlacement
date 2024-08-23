# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n<sup>3</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n<sup>2</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution{
    public:
    int solve(int i, int j, int *keys, int *freq, vector<vector<int>> &dp){
    
        if(i==j){
            return freq[i];
        }
        if(i>j){
            return 0;
        }
        if(dp[i][j]!=-1){
            return dp[i][j];
        }
    
        int cur=0;
        for(int k=i;k<=j;k++){
            cur += freq[k];
        }
    
        int ans=INT_MAX;
        for(int k=i;k<=j;k++){
            int left=solve(i,k-1,keys,freq,dp);
            int right=solve(k+1,j,keys,freq,dp);
            
            ans=min(ans, left + right + cur);
        }
        return dp[i][j]=ans;
    }
    int optimalSearchTree(int keys[], int freq[], int n)
    {
        // code here
        vector<vector<int>>dp(n,vector<int>(n,-1));
        return solve(0,n-1,keys,freq,dp);
    }
};
```
