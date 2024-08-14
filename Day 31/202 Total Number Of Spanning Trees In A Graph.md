# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n<sup>4</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n<sup>2</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution{
    public:
    int determinant(vector<vector<int>> matrix){
        int det=0;
        if(matrix.size()==1)
            return matrix[0][0];
        
        else if(matrix.size()==2)
            return matrix[0][0]*matrix[1][1]-matrix[1][0]*matrix[0][1];
            
        for(int p=0;p<matrix[0].size();p++){
            vector<vector<int>>temp;
            for(int i=1;i<matrix.size();i++){
                vector<int>row;
                for(int j=0;j<matrix[0].size();j++){
                    if(p!=j)
                        row.push_back(matrix[i][j]);
                }
                if(row.size()>0)
                    temp.push_back(row);
            }
            det=det+matrix[0][p]*pow(-1,p)*determinant(temp);
        }
        return det;
    }
    int countSpanningTrees(vector<vector<int>>&graph, int n, int m){
        //Write your code here 
        vector<int>degree(n,0);
        vector<vector<int>> LaplacianMatrix(n,vector<int>(n,0));
        for(auto it : graph){
            LaplacianMatrix[it[0]][it[1]] = -1;
            LaplacianMatrix[it[1]][it[0]] = -1;
            degree[it[0]]++;
            degree[it[1]]++;
        }
        for(int i=0;i<n;i++)
            LaplacianMatrix[i][i]=degree[i];
            
        vector<vector<int>>ansMatrix(n-1,vector<int>(n-1));
        for (int i=1;i<n;i++){
            for(int j=1;j<n;j++)
                ansMatrix[i-1][j-1]=LaplacianMatrix[i][j];
        }
        
        return determinant(ansMatrix);
    }
};
```
