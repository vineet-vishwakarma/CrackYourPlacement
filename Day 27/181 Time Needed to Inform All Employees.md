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
    int dfs(int id,vector<int>&visited,vector<int>adj[],vector<int>&it){
        visited[id]=1;
        int ans=it[id];
        int maxi=0;
        for(auto i:adj[id]){
            if(!visited[i]){
                maxi=max(maxi,dfs(i,visited,adj,it));
            }
        }
        return ans+maxi;
    }
    int numOfMinutes(int n, int headID, vector<int>& manager, vector<int>& informTime) {
        vector<int>adj[n];
        for(int i=0;i<n;i++){
            if(manager[i]!=-1){
                adj[manager[i]].push_back(i);
            }
        }
        vector<int>visited(n,0);
        visited[headID]=1;
        return dfs(headID,visited,adj,informTime);
    }
};
```