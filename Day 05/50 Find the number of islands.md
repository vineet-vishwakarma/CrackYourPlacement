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
    int n=0;
    int m=0;
    void dfs(vector<vector<char>>& grid, int i,int j){        
        if(i<0 || i>=n || j<0 || j>=m || grid[i][j]=='0'){
            return;
        }

        grid[i][j]='0';

        dfs(grid,i+1,j);
        dfs(grid,i-1,j);
        dfs(grid,i,j+1);
        dfs(grid,i,j-1);
        
        dfs(grid,i+1,j+1);
        dfs(grid,i-1,j-1);
        dfs(grid,i+1,j-1);
        dfs(grid,i-1,j+1);
    }
    
    int numIslands(vector<vector<char>>& grid) {
        // Code here
        n=grid.size();
        m=grid[0].size();
        int ans=0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]=='1'){
                    ans++;
                    dfs(grid,i,j);
                }
            }
        }
        return ans;
    }
};
```
