# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(V + E)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(V)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    void dfs(vector<vector<int>>&adj,vector<bool>&visited,int i){
        visited[i]=true;
        for(auto n:adj[i]){
            if(!visited[n])
                dfs(adj,visited,n);
        }
    }
    int makeConnected(int n, vector<vector<int>>& connections) {
        if(connections.size()<n-1)
            return -1;
        
        vector<vector<int>>adj(n);
        for(auto i:connections){
            adj[i[0]].push_back(i[1]);
            adj[i[1]].push_back(i[0]);
        }
        vector<bool>visited(n,false);
        int ans=-1;

        for(int i=0;i<n;i++){
            if(!visited[i]){
                dfs(adj,visited,i);
                ans++;
            }
        }
        return ans;
    }
};
```