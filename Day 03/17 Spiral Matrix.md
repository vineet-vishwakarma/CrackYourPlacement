# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int>ans;
        int rows = matrix.size();
        int cols = matrix[0].size();
        
        int total = rows*cols;
        int count = 0;

        int sRow = 0;
        int sCol = 0;
        int eRow = rows-1;
        int eCol = cols-1;

        while(count<total){
            for(int i=sCol;i<=eCol && count<total;i++){
                ans.push_back(matrix[sRow][i]);
                count++;
            }
            sRow++;

            for(int i=sRow;i<=eRow && count<total;i++){
                ans.push_back(matrix[i][eCol]);
                count++;
            }
            eCol--;

            for(int i=eCol;i>=sCol && count<total;i--){
                ans.push_back(matrix[eRow][i]);
                count++;
            }
            eRow--;

            for(int i=eRow;i>=sRow && count<total;i--){
                ans.push_back(matrix[i][sCol]);
                count++;
            }
            sCol++;
        }
        return ans; 
    }
};
```