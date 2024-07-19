# Approach 
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution{
public:
    void dfs(int i,int j,vector<vector<char>> &mat,vector<vector<int>>&visited,int n,int m){
        if(i<0 || j<0 || i>=n || j>=m || mat[i][j]=='X' || visited[i][j]==1) 
            return;
            
        visited[i][j] = 1;
        
       dfs(i+1,j,mat,visited,n,m);
       dfs(i-1,j,mat,visited,n,m);
       dfs(i,j+1,mat,visited,n,m);
       dfs(i,j-1,mat,visited,n,m);
    }
    
    vector<vector<char>> fill(int n, int m, vector<vector<char>> mat)
    {
        // code here
        vector<vector<int>>visited(n,vector<int>(m,0));
        
        for(int i=0;i<n;i++){
            if(mat[i][0]=='O' && !visited[i][0]) 
               dfs(i, 0, mat, visited, n, m);
            if(mat[i][m-1]=='O'&& !visited[i][m-1]) 
               dfs(i,m-1,mat,visited,n,m);
        }
        
        for(int j=0;j<m;j++){
            if(mat[0][j]=='O' && !visited[0][j]) 
               dfs(0,j,mat,visited,n,m);
            if(mat[n-1][j]=='O' && !visited[n-1][j]) 
               dfs(n-1,j,mat,visited,n,m);
        }
       
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(mat[i][j]=='O' && visited[i][j]==0){
                    mat[i][j]='X';
                }
            }
        }
    
        return mat;
    }
};
```
