# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n!*n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n!)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        set<vector<int>>s;
        vector<vector<int>>ans;
        
        sort(nums.begin(),nums.end());
        
        do{
            s.insert(nums);
        }while(next_permutation(nums.begin(),nums.end()));

        for(auto i:s){
            ans.push_back(i);
        }
        return ans;
    }
};
```
