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
    int ans=INT_MIN;
    int solve(string &str1,string &str2,int i,int j,vector<vector<int>>&dp){
        if(i>=str1.size() || j>=str2.size()){
            return 0;
        }
        
        if(dp[i][j]!=-1){
            return dp[i][j];
        }
        
        int curr=0;
        if(str1[i]==str2[j]){
            curr=1+solve(str1,str2,i+1,j+1,dp);
            ans=max(curr,ans);
        }
        
        solve(str1,str2,i,j+1,dp);
        solve(str1,str2,i+1,j,dp);    
        
        return dp[i][j]=curr;
    }
    int longestCommonSubstr(string str1, string str2) {
        // your code here
        int i=0;
        int j=0;
        vector<vector<int>>dp(str1.size()+1,vector<int>(str2.size()+1,-1));
        
        solve(str1,str2,i,j,dp);
        return ans==INT_MIN?0:ans;
    }
};
```
