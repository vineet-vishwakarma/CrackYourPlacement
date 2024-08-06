# Complexity
- Time Complexity: O(v+e)
- Space Complexity: O(v)

# Code
```
class Solution {
  public:
    // Function to return a list containing the DFS traversal of the graph.
    vector<int>ans;
    vector<bool>visited;
    
    void dfs(int node,vector<int>adj[]){
        visited[node]=true;
        ans.push_back(node);
        
        for(auto i:adj[node]){
            if(!visited[i]){
                dfs(i,adj);
            }
        }
    }
    
    vector<int> dfsOfGraph(int V, vector<int> adj[]) {
        // Code here
        visited.resize(V);
        dfs(0,adj);
        return ans;
    }
};
```
