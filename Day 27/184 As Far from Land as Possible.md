# Approach
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
    int maxDistance(vector<vector<int>>& grid) {
        int n=grid.size();
        queue<pair<int,int>>q;
        vector<vector<int>>visited=grid;
        
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(visited[i][j]==1) 
                    q.push({i,j});
            }
        }

        if(q.empty() || q.size()==n*n) 
            return -1;

        int distance=-1;

        vector<pair<int,int>>dirs={{0, 1},{0, -1},{1, 0},{-1, 0}};
        
        while(!q.empty()){
            int s=q.size();
            while(s--){
                auto[x,y]=q.front();
                q.pop();

                for(auto [dx, dy]:dirs){
                    int i=x+dx; 
                    int j=y+dy;

                    if(i>=0 && i<n && j>=0 && j<n && visited[i][j]==0){
                        visited[i][j]=1;
                        q.push({i,j});
                    }
                }
            }
            distance++;
        }
        return distance;
    }
};
```
