# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int findMaxSquare(vector<vector<char>>& matrix,int i,int j,int& maxLength,vector<vector<int>>&dp){
        // base case
        if(i>=matrix.size() || j>=matrix[0].size()){
            return 0;
        }

        if(dp[i][j]!=-1){
            return dp[i][j];
        }

        int right=findMaxSquare(matrix,i,j+1,maxLength,dp);
        int daigonal=findMaxSquare(matrix,i+1,j+1,maxLength,dp);
        int down=findMaxSquare(matrix,i+1,j,maxLength,dp);

        if(matrix[i][j]=='1'){
            dp[i][j]=1+min(right,min(daigonal,down));
            maxLength=max(maxLength,dp[i][j]);
            return dp[i][j];
        }
        return dp[i][j]=0;
    }
    int maximalSquare(vector<vector<char>>& matrix) {
        int maxLength=0;
        vector<vector<int>>dp(matrix.size(),vector<int>(matrix[0].size(),-1));
        findMaxSquare(matrix,0,0,maxLength,dp);
        return maxLength*maxLength;
    }
};
```
