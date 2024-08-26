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
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>>ans={{}};
        for(int num:nums){
            int n=ans.size();
            for(int i=0;i<n;i++){
                ans.push_back(ans[i]); 
                ans.back().push_back(num);
            }
        }
        return ans;
    }
};
```
