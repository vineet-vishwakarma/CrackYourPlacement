# Approach 1 (Using Map)
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
    vector<int> findDuplicates(vector<int>& nums) {
        unordered_map<int,int>mp;
        vector<int>ans;

        for(auto i:nums){
            mp[i]++;
        }
        for(auto i:mp){
            if(i.second>1){
                ans.push_back(i.first);
            }
        }
        return ans;
    }
};
```

# Approach 2 (Seat Reserving Logic)
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector<int>ans;
        
        for(int i=0;i<nums.size();i++){
            int element=abs(nums[i]);
            int seat = element-1;

            if(nums[seat]<0){
                ans.push_back(abs(nums[i]));
            }
            else{
                nums[seat]=-nums[seat];
            }
        }
        return ans;
    }
};
```
