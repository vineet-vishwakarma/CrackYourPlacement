# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O((N*(2<sup>N</sup>))/K)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int solve(vector<int> &stones,int i,int j,int k,vector<int> &pre,vector<vector<int>> &dp){
        if(i>=j)
            return 0;

        if(dp[i][j]!=-1){
            return dp[i][j];
        }

        int ans=INT_MAX;
        
        for(int index=i;index<j;index=index+k-1){
            int tmp=solve(stones,i,index,k,pre,dp)+solve(stones,index+1,j,k,pre,dp);
            ans=min(ans,tmp);
        }
        
        if((j-i)%(k-1)==0){
            ans=ans+pre[j+1]-pre[i];
        }
        return dp[i][j]=ans;
    }
    int mergeStones(vector<int>& stones, int k) {
        int n=stones.size();
        if((n-1)%(k-1)!=0){
            return -1;
        }
        //calculate the prefix sum
        vector<int> pre(n+1,0);
        for(int i=1;i<=n;i++){
            pre[i]=pre[i-1]+stones[i-1];
        }

        //dp vector for memoization
        vector<vector<int>> dp(n+1,vector<int>(n+1,-1));
        return solve(stones,0,n-1,k,pre,dp);
    }
};
```
