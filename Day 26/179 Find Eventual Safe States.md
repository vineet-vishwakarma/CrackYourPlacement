# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(V+E)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(V+E)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    bool dfs(vector<vector<int>>&adj,int src,vector<bool>&visited,vector<bool>&pathVisited){
        visited[src]=true;
        pathVisited[src]=true;
        for(auto i:adj[src]){
            if(!visited[i] && dfs(adj,i,visited,pathVisited)){
                return true;
            }
            else if(pathVisited[i]){
                return true;
            }
        }
        pathVisited[src]=false;
        return false;
    }
    vector<int> eventualSafeNodes(vector<vector<int>>& graph) {
        int n=graph.size();
        vector<vector<int>>adj(n);
        for(int i=0;i<n;i++){
            for(int j=0;j<graph[i].size();j++){
                adj[i].push_back(graph[i][j]);
            }
        }

        vector<bool>visitedited(n,false);
        vector<bool>pathvisitedited(n,false);

        for(int i=0;i<n;i++){
            if(!visitedited[i]){
                dfs(adj,i,visitedited,pathvisitedited);
            }
        }
        vector<int>ans;
        for(int i=0;i<pathvisitedited.size();i++){
            if(!pathvisitedited[i]){
                ans.push_back(i);
            }
        }
        return ans;
    }
};
```
