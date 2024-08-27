# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(4<sup>k</sup>)where 𝑘 is the number of empty cells
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int m,n;
    vector<int> dx={-1,1,0,0};
    vector<int> dy={0,0,-1,1};
    
    bool isvalid(int i, int j){
        return i >= 0 && j >= 0 && i < m && j < n;
    }

    int dfs(int i, int j, int left, pair<int, int> dest, vector<vector<int>> &grid){
        // Base case
        if(left==-1 && pair<int,int>(i,j)==dest)
            return 1;

        // Mark visited
        grid[i][j]=-1;

        int ans=0;
        for(int k=0;k<4;k++){
            int x=i+dx[k];
            int y=j+dy[k];

            if(isvalid(x, y) && grid[x][y]!=-1)
                ans+=dfs(x,y,left-1,dest,grid);
        }

        // Backtrack
        grid[i][j]=0;
        return ans;
    }
    int uniquePathsIII(vector<vector<int>>& grid) {
        m=grid.size();
        n=grid[0].size();

        pair<int,int>src,dest;
        int empty=0;

        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]==0)
                    empty++;
                if(grid[i][j]==1)
                    src={i,j};
                if(grid[i][j] == 2)
                    dest={i, j};
            }
        }

        return dfs(src.first, src.second, empty, dest, grid);
    }
};
```
