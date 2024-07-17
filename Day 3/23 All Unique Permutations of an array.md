# Approach (Moore's Voting Algorithm)
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*n!)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*n!)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public:
    vector<vector<int>> uniquePerms(vector<int> &arr ,int n) {
        // code here
        sort(arr.begin(),arr.end());
        vector<vector<int>>ans;
        
        do{
            ans.push_back(arr);
        }while(next_permutation(arr.begin(),arr.end()));
        
        return ans;
    }
};
```
