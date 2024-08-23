# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*k)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*k)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int solve(vector<int> &prices,int ind,bool buy,int c,int k, vector<vector<vector<int>>> &dp)
    {   
        if(ind>=prices.size()||c>=k) 
            return 0;
        else if(dp[ind][buy][c]!=-1) 
            return dp[ind][buy][c];
         
        if(buy){
            return dp[ind][buy][c]=max(-prices[ind]+solve(prices,ind+1,!buy,c,k,dp),solve(prices,ind+1,buy,c,k,dp));
        }else{
            return dp[ind][buy][c]=max(prices[ind]+solve(prices,ind+1,!buy,c+1,k,dp),solve(prices,ind+1,buy,c,k,dp));
        }
        
    }
    int maxProfit(int k, vector<int>& prices) {
        if(2*k>prices.size()){
            int ans=0;
            for(int i=1;i<prices.size();i++){
                ans+=max(0,prices[i]-prices[i-1]);
            }
            return ans;
        }
        
        vector<vector<vector<int>>>dp(prices.size()+1,vector<vector<int>>(2,vector<int>(k+1,-1)));
        return solve(prices,0,1,0,k,dp); 
    }
};
```
