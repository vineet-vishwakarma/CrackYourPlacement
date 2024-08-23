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
    int MCM(vector<int>& nums, int left,int right, vector<vector<int>>& mem){
        if(left>=right)
            return 0;
        
        if(mem[left][right]!=-1)
            return mem[left][right];
        
        int max_cost=INT_MIN;
        
        for(int k=left;k<right;k++)
        {
        int total_cost=MCM(nums,left,k,mem)+MCM(nums,k+1,right,mem)+nums[left-1]*nums[k]*nums[right];    
        max_cost=max(max_cost,total_cost);
            mem[left][right]=max_cost;
        }
        return mem[left][right];
    }
    int maxCoins(vector<int>& nums) {
        nums.insert(nums.begin(),1);
        nums.push_back(1);
        
        int n=nums.size();
        vector<vector<int>> mem(n,vector<int>(n,-1));
        
        return MCM(nums,1,n-1,mem);
    }
};
```
