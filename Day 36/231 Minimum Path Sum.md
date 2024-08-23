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
    int minPathSum(vector<vector<int>>& grid) {
        int m=grid.size();
        int n=grid[0].size();
        
        vector<int>cur(m,grid[0][0]);
        
        for(int i=1;i<m;i++){
            cur[i]=cur[i-1]+grid[i][0]; 
        }

        for (int j=1;j<n;j++){
            cur[0]+=grid[0][j]; 
            for(int i=1;i<m;i++)
                cur[i]=min(cur[i-1],cur[i])+grid[i][j];
        }
        
        return cur[m-1];
    }
};
```