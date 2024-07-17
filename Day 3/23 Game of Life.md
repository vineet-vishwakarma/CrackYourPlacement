# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m*8)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int liveNeighbours(vector<vector<int>>& curr, int i, int j, int m, int n) {
        int liveNeighbours=0;
        
        if(i>0){
            if(curr[i-1][j]==1) 
                liveNeighbours++;
        }
        if(i<m-1){
            if(curr[i+1][j]==1) 
                liveNeighbours++;
        }
        if(j>0){
            if(curr[i][j-1]==1) 
                liveNeighbours++;
        }
        if(j<n-1){
            if(curr[i][j+1]==1) 
                liveNeighbours++;
        }

        if(i>0 && j>0){
            if(curr[i-1][j-1]==1) 
                liveNeighbours++;
        }
        if(i>0 && j<n-1){
            if(curr[i-1][j+1]==1) 
                liveNeighbours++;
        }
        if(i<m-1 && j>0){
            if(curr[i+1][j-1]==1) 
                liveNeighbours++;
        }
        if(i<m-1 && j<n-1){
            if(curr[i+1][j+1]==1) 
                liveNeighbours++;
        }
        return liveNeighbours;
    }

    void gameOfLife(vector<vector<int>>& board) {
        int n = board.size();
        int m = board[0].size();
        vector<vector<int>> v(n, vector<int>(m,0));

        for (int i=0;i<n;i++) {
            for (int j=0;j<m;j++) {
                int sum = liveNeighbours(board,i,j,n,m);
                
                if(sum<2 && board[i][j]==1)
                    v[i][j]=0;
                else if(board[i][j]==1 && sum>=2 && sum<=3)
                    v[i][j]=1;
                else if(board[i][j]==1 && sum>3)
                    v[i][j]=0;
                else if(board[i][j]==0 && sum==3)
                    v[i][j]=1;
            }
        }

        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                board[i][j]=v[i][j];
            }
        }
    }
};
```
