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
    void solve(int n, int k, vector<vector<int>> &ans, vector<int> &temp, int s){
        if(temp.size()==k){
            ans.push_back(temp);
            return;
        }
        for(int i=s;i<=n;i++){
            temp.push_back(i);
            solve(n,k,ans,temp,i+1);
            temp.pop_back();
        }
    } 
    vector<vector<int>>combine(int n, int k) {
        vector<vector<int>>ans;
        vector<int>temp;
        solve(n,k,ans,temp,1);
        return ans;
    }
};
```
