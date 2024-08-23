# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class NumMatrix {
public:
    int n,m;
    vector<vector<int>>sums;

    NumMatrix(vector<vector<int>>& matrix) {
        n=matrix.size();
        m=n>0 ? matrix[0].size() : 0;
        sums = vector<vector<int>>(n+1,vector<int>(m+1,0));
        for(int i=1; i<=n; i++){
            for(int j=1; j<=m; j++){
                sums[i][j] = matrix[i-1][j-1]+sums[i-1][j]+sums[i][j-1]-sums[i-1][j-1];
            }
        }
    }
    
    int sumRegion(int row1, int col1, int row2, int col2) {
        return sums[row2+1][col2+1]-sums[row2+1][col1]-sums[row1][col2+1]+sums[row1][col1];
    }
};

/**
 * Your NumMatrix object will be instantiated and called as such:
 * NumMatrix* obj = new NumMatrix(matrix);
 * int param_1 = obj->sumRegion(row1,col1,row2,col2);
 */
```