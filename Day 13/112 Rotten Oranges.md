# Approach (BFS)
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution 
{
    public:
    //Function to find minimum time required to rot all oranges. 
    int orangesRotting(vector<vector<int>>& grid) {
        // Code here
        queue<pair<int,int>>q;
        
        int n=grid.size();
        int m=grid[0].size();
        
        int freshOranges=0;
        
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]==2)
                    q.push({i,j});
                else if(grid[i][j]==1)
                    freshOranges++;
            }
        }
    
        int ans=0;
        vector<pair<int,int>>dirs={{0,1},{1,0},{-1,0},{0,-1}};
        
        while(freshOranges!=0 && !q.empty()){
            int s=q.size();
            
            for(int i=0;i<s;i++){
                int newX=q.front().first;
                int newY=q.front().second;
                q.pop();
                
                for(auto d:dirs){
                    int x = newX+d.first; 
                    int y = newY+d.second; 
                    
                    if(x>=0 && x<n && y>=0 && y<m && grid[x][y]==1){
                        grid[x][y]=2;
                        freshOranges--;
                        q.push({x,y});
                    }
                }
            }
            ans++;
        }
        
        return freshOranges==0?ans:-1;
    }
};
```
