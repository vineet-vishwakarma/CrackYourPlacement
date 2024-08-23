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
    int countSquares(vector<vector<int>>& matrix) {
        int m = matrix.size();
        int n = matrix[0].size();

        vector<vector<int>> dp = matrix;

        for(int i = 1; i < m; i++){
            for(int j = 1; j < n; j++){
                if(matrix[i][j] != 0){
                    dp[i][j] = min(dp[i-1][j-1], min(dp[i-1][j], dp[i][j-1])) + 1;
                }
                
            }
        }
        int answer = 0;
        for(int i = 0; i < m; i++){
            answer += accumulate(dp[i].begin(), dp[i].end(), 0);
        }

        return answer; 
    }
};
```
