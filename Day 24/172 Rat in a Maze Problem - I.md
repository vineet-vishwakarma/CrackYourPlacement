# Complexity
- Time Complexity: O(3<sup>n<sup>2</sup></sup>)
- Time Complexity:

# Code
```
class Solution {
  public:
    bool isSafe(int newx,int newy,vector<vector<int>> &arr,vector<vector<bool>>&visited,int n){
        if(newx>=0 && newx<n && newy>=0 && newy<n && visited[newx][newy]==0 && arr[newx][newy]==1){
            return true;
        }
        return false;
    }    
    
    void solve(int x,int y,vector<vector<int>> &arr,int n,vector<string> &ans, vector<vector<bool>> &visited,string path){
        if(x==n-1 && y==n-1){
            ans.push_back(path);
            return;
        }
        
        visited[x][y]=true;
        
        // Down
        if(isSafe(x+1,y,arr,visited,n)){
            solve(x+1,y,arr,n,ans,visited,path+"D");
        }
        
        // Right
        if(isSafe(x,y+1,arr,visited,n)){
            solve(x,y+1,arr,n,ans,visited,path+"R");
        }
        // Left
        if(isSafe(x,y-1,arr,visited,n)){
            solve(x,y-1,arr,n,ans,visited,path+"L");
        }
        
        
        // Up
        if(isSafe(x-1,y,arr,visited,n)){
            solve(x-1,y,arr,n,ans,visited,path+"U");
        }
        
        visited[x][y]=false;
        
    }
    vector<string> findPath(vector<vector<int>> &mat) {
        // Your code goes here
        vector<string>ans;
        int n=mat.size();
        if(mat[0][0]==0)
            return ans;
        
        vector<vector<bool>>visited(n,vector<bool>(n,0));
        string path="";
        
        solve(0,0,mat,n,ans,visited,path);
        return ans;
    }
};
```
