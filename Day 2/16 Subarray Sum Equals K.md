# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int ans=0;
        int sum=0;
        
        unordered_map<int,int>mp;
        mp[0]=1;
        int n=nums.size();
        
        for(int i=0;i<n;i++){
            sum+=nums[i];
            int rem=sum-k;
            
            if(mp.contains(rem)){
                ans+=mp[rem];
            }
            mp[sum]++;
        }
        return ans;
    }
};
```
