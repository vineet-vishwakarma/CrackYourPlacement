# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    
    int lis(vector<int>& nums,int i,int last,vector<vector<int>> &dp){
        if(i==nums.size())
            return 0;

        if(dp[i][last+1] != -1){
            return dp[i][last+1];
        }

        int pick=0;
        if(last==-1 || nums[last]<nums[i]){
            pick=1+lis(nums,i+1,i,dp);
        }
        int noPick=0;
        noPick=0+lis(nums,i+1,last,dp);

        dp[i][last+1] = max(pick,noPick);
        return dp[i][last+1];
    }
    int lengthOfLIS(vector<int>& nums) {
        int last=INT_MIN;
        int n=nums.size();
        vector<vector<int>> dp(n+1,vector<int>(n+1,-1));
        return lis(nums,0,-1,dp);
    }
};
```