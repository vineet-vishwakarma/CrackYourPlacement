# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n\*k\*logn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*k)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int recur(int k, int n, vector<vector<int>>& dp){
        if(n==0 || n==1) 
            return n;
        if(k==1) 
            return n;
        
        if(dp[k][n]!=-1) 
            return dp[k][n];
        
        int mini = INT_MAX, low = 0, high = n, temp = 0;
        
        while(low<=high){
            
            int mid = (low + high)/2;
            int left = recur(k-1, mid-1, dp);
            int right = recur(k, n-mid, dp);
            
            temp = 1 + max(left, right);
            
            if(left < right) 
                low = mid+1;
            else 
                high = mid-1;     
    
            mini = min(mini, temp); 
        }
        return dp[k][n] = mini;
    }
    int superEggDrop(int k, int n) {
        vector<vector<int>> dp(k+1, vector<int>(n+1, -1));
        return recur(k, n, dp);
    }
};
```
