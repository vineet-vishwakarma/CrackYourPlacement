# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(N<sup>2</sup>*k)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    bool isValid(int x,int y,int n,vector<vector<int>>&m){
        return(x>=0 && x<n && y>=0 && y<n && m[x][y]!=0); 
    }
    
    bool dfs(vector<vector<int>>&m,vector<vector<int>>&visited, int x,int y,int n){
        if(x==n-1 && y==n-1){
            visited[x][y]=1;
            return true;
        }
        if(isValid(x,y,n,m) && !visited[x][y]){
            visited[x][y]=1;
            for(int i=1;i<=m[x][y] && i<n;i++){
                if(dfs(m,visited,x,y+i,n)) 
                    return true;
                if(dfs(m,visited,x+i,y,n)) 
                    return true;
            }
            visited[x][y]=0;
            return false;
        } 
        return false;
    }
    vector<vector<int>> ShortestDistance(vector<vector<int>>&m){
           // Code here
        int n=m.size();
        vector<vector<int>>visited(n,vector<int>(n,false));
        
        if(!dfs(m,visited,0,0,n)) 
            return {{-1}};
        
        return visited;
	}
```
