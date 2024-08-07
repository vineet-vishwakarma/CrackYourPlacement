# Complexity
- Time Complexity: O(V+E)
- Space Complexity: O(V)

# Code
```
class Solution {
  public:
    // Function to detect cycle in an undirected graph.
    bool dfs(vector<int>adj[],int curr,int parent,vector<bool>&visited){
        visited[curr]=true;
        bool flag=false;
        for(auto x:adj[curr]){
           if(!visited[x]){
               flag|=dfs(adj,x,curr,visited);
           }
           else if(visited[x] && x!=parent){
               return true;
           }
        }
        return flag;
    }
    bool isCycle(int V, vector<int> adj[]) {
        // Code here
        vector<bool>visited(V,false);
        for(int i=0;i<V;i++){
            if(!visited[i] && dfs(adj,i,-1,visited)){
                return true;
            }
        }
        return false;
    }
};
```
