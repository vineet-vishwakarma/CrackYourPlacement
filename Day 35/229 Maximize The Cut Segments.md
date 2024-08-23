# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution
{
    public:
    //Function to find the maximum number of cuts.
    int solve(int n,int x,int y,int z,vector<int>&dp){
        if(n==0)
            return 0;
            
        if(n<0)
            return INT_MIN;
            
        if(dp[n]!=-1)
            return dp[n];
            
        int a=INT_MIN;
        if(n-x>=0)
            a=1+solve(n-x,x,y,z,dp);
            
        int b=INT_MIN;
        if(n-y>=0)
            b=1+solve(n-y,x,y,z,dp);
        
        int c=INT_MIN;
        if(n-z>=0)
            c=1+solve(n-z,x,y,z,dp);
        
        return dp[n]=max(a,max(b,c));
    }
    int maximizeTheCuts(int n, int x, int y, int z)
    {
        //Your code here
        vector<int>dp(n+1,-1);
        
        int ans=solve(n,x,y,z,dp);
        
        if(ans<0)
            return 0;
            
        return ans;
    }
};
```
