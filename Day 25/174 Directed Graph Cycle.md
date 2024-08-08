# Complexity
- Time Complexity: O(V+E)
- Space Complexity: O(V)

# Code
```
class Solution {
  public:
    // Function to detect cycle in a directed graph.
    bool dfs(vector<int> adj[],int curr,int parent,vector<bool>&visited,vector<bool>&pathVisited){
        visited[curr]=true;
        pathVisited[curr]=true;
        
        for(auto i:adj[curr]){
            if(!visited[i]){
                if(dfs(adj,i,curr,visited,pathVisited)){
                    return true;
                }
            }else if(pathVisited[i]){
                return true;
            }
        }
        
        pathVisited[curr]=false;
        return false;
    }
    
    bool isCyclic(int V, vector<int> adj[]) {
        // code here
        vector<bool>visited(V,false);
        vector<bool>pathVisited(V,false);
        
        for(int i=0;i<V;i++){
            if(!visited[i]){
                if(dfs(adj,i,-1,visited,pathVisited)){
                    return true;
                }
            }
        }
        return false;
    }
};
```