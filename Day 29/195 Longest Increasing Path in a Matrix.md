# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int n,m;
    int solve(int row, int col, vector<vector<int>> & mat, vector<vector<int>> & dp) {
        int delrow[]={-1,0,1,0};
        int delcol[]={0,1,0,-1};
        int maxi=0;
        
        if(dp[row][col]!=-1)
            return dp[row][col];

        for(int i=0;i<4;i++){
            int drow=delrow[i]+row;
            int dcol=delcol[i] + col;
            if(drow>=0 && dcol>=0 && drow<n && dcol<m && mat[drow][dcol]>mat[row][col]){
                maxi=max(maxi,1+solve(drow,dcol,mat,dp));
            }
        }
        return dp[row][col]=maxi;
    }
    int longestIncreasingPath(vector<vector<int>>& matrix) {
        n=matrix.size();
        m=matrix[0].size();
        vector<vector<int>>dp(n,vector<int>(m,-1));
        int ans=0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                ans=max(ans,solve(i,j,matrix,dp));
            }
        }
        return ans+1;
    }
};
```
