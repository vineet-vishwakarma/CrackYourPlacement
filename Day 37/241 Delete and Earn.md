# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int deleteAndEarn(vector<int>& nums) {
        vector<int>cnt(10002);

    		for(int i=0;i<nums.size();i++){
    			cnt[nums[i]]+=nums[i];
    		}
    
    		vector<int>dp(10002);
    		
            dp[1]=cnt[1];
    		dp[2]=max(cnt[1],cnt[2]);
    		
            for(int i=3;i<dp.size();i++){
    			dp[i]=max(dp[i-2]+cnt[i],dp[i-1]);
    		}
    
    		return max(dp[10000],dp[9999]);
    }
};
```
