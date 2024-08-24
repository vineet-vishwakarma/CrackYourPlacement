# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*amount)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(amount)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution{
	public:
	int MinCoin(vector<int>nums, int amount)
	{
	    // Code here
	    vector<int>dp(amount+1,INT_MAX);
	    dp[0] = 0;
	    for(int t=1; t<=amount; t++){
	        int mini = INT_MAX;
	        for(int i=0; i<nums.size(); i++){
	            if(t - nums[i] >= 0){
	                int ans = dp[t-nums[i]];
	                if(ans != INT_MAX){
	                    mini = min(mini,1+ans);
	                }
	            }
	        }
	        dp[t]=mini;
	    }
	    
	    return dp[amount]==2147483647?-1:dp[amount];
	}
};
```
