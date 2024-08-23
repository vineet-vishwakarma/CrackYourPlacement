# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int dp[12+1][10000+1];
    
    int findLowestCoins(vector<int> &coins,int n,int amount){
        for(int i=0;i<n+1;i++){
            for(int j=0;j<amount+1;j++){
                if (i==0 || j==0)
                    dp[i][j]=(j==0)?0:INT_MAX-1;
            }
        }
        
        for(int i=1;i<n+1;i++){
            for (int j=1;j<amount+1;j++){
                if(coins[i-1]>j)
                    dp[i][j]=0+dp[i-1][j];
                else
                    dp[i][j]=min(0+dp[i-1][j],1+dp[i][j-coins[i-1]]);
            }
        }
        
        return dp[n][amount];
    }
    int coinChange(vector<int>& coins, int amount) {
        int ans=findLowestCoins(coins,coins.size(),amount);
        return (ans==INT_MAX-1)?-1:ans;
    }
};
```
