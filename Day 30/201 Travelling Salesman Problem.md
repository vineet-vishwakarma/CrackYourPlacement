# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(2<sup>n</sup> * n<sup>2</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(2<sup>n</sup> * n<sup>2</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int n;
    int solve(int ind,vector <vector <int>> &cost,int mask,vector <vector <int>> &dp){
        
        mask=mask^(1<<ind);
        
        if(mask==0)
            return cost[ind][0];
        
        if(dp[ind][mask]!=-1)
            return dp[ind][mask];
            
        int ans=INT_MAX;
        for(int j=0;j<n;j++){
            if(mask&(1<<j)){
                ans=min(ans,cost[ind][j]+solve(j,cost,mask,dp));
            }
        }
        
        return dp[ind][mask]=ans;
    }
    int total_cost(vector<vector<int>>cost){
        // Code here
        n=cost.size();
        int mask=pow(2,n)-1;
        vector <vector<int>>dp(n,vector<int>(mask+1,-1));
        return solve(0,cost,mask,dp);
    }
};
```
