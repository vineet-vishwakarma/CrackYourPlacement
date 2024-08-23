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
    long long dfs(long long start , int n,map <long long, vector <long long>> &mp,vector <vector<long long>> &dp){
      if(n==1){
          return 1;
      }
      
      if(dp[start][n] != -1){
          return dp[start][n];
      }
      
      vector <long long> v = mp[start];
      long long curr=0;
      for(int i =0  ; i < v.size() ; i++){
          curr += dfs(v[i],n-1,mp,dp);
      }
      return (dp[start][n]=curr);
    }
    long long getCount(int n) {
        // Your code goes here
        map <long long, vector <long long>> mp;
        vector <vector<long long>> dp(10,vector <long long>(n+1,-1));
        
        mp[1] = {1,2,4};
        mp[2] = {2,1,3,5};
        mp[3] = {3,2,6};
        mp[4] = {4,1,5,7};
        mp[5] = {5,2,4,6,8};
        mp[6] = {6,3,5,9};
        mp[7] = {7,8,4};
        mp[8] = {8,7,5,9,0};
        mp[9] = {9,6,8};
        mp[0] = {0,8};
        
        long long curr=0;
        for(int i =0 ; i < 10 ; i++){
            long long h = dfs(i,n,mp,dp);
            curr+=h;
        }
        return curr;
    }
};
```
