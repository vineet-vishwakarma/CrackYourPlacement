# Approach Multisource BFS
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n<sup>2</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n<sup>2</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    void dfs(vector<vector<int>>& grid,vector<vector<bool>>& visited,queue<pair<int,int>>&q,int i,int j,vector<pair<int,int>>dirs){
        if(i<0 || j<0 || i>=grid.size() || j>=grid[0].size() || visited[i][j] || grid[i][j]==0){
            return;
        }

        visited[i][j]=true;
        q.push({i,j});
        for(auto dir:dirs){
            dfs(grid,visited,q,i+dir.first,j+dir.second,dirs);
        }

    }
    int shortestBridge(vector<vector<int>>& grid) {
        int n=grid.size();
        int m=grid[0].size();

        vector<vector<bool>>visited(n,vector<bool>(m,false));
        queue<pair<int,int>>q;
        vector<pair<int,int>>dirs={{0,1},{0,-1},{-1,0},{1,0}};
        
        bool flag=false;

        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]==1){
                    dfs(grid,visited,q,i,j,dirs);
                    flag=true;
                    break;
                }
            }
            if(flag)
                break;
        }

        int ans=0;
        while(!q.empty()){
            int s=q.size();
            for(int i=0;i<s;i++){
                auto curr=q.front();
                q.pop();

                int x=curr.first;
                int y=curr.second;

                for(auto dir:dirs){
                    int newX=x+dir.first;
                    int newY=y+dir.second;

                    if(newX>=0 && newX<n && newY>=0 && newY<m && !visited[newX][newY]){
                        if(grid[newX][newY]==1){
                            return ans;
                        }
                        q.push({newX,newY});
                        visited[newX][newY]=true;
                    }

                }
            }
            ans++;
        }
        return -1;
    }
};
```
