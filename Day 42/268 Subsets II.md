# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(2<sup>n</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(2<sup>n</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    void solve(vector<int>&nums,vector<vector<int>>&ans,vector<int>& curr,int s){
        ans.push_back(curr);
        for(int i=s;i<nums.size();i++){

            if(i>s && nums[i]==nums[i-1]) 
                continue;      

            curr.push_back(nums[i]);
            solve(nums,ans,curr,i+1); 
            curr.pop_back();         
        }
    }  
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<vector<int>>ans;
        vector<int>curr;
        sort(nums.begin(),nums.end());
        solve(nums,ans,curr,0);
        return ans;
    }
};
```
