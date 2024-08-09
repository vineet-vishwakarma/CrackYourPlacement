# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(V+E)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(V+E)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution
{   
    void dfs(int curr,vector<vector<int>>& adj,vector<bool>&visited,stack<int>&st){
        visited[curr]=true;
        
        for(auto i:adj[curr]){
            if(!visited[i]){
                dfs(i,adj,visited,st);
            }
        }
        
        st.push(curr);
    }
    void dfs2(int curr,vector<vector<int>>& adj,vector<bool>&visited){
        visited[curr]=true;
        
        for(auto i:adj[curr]){
            if(!visited[i]){
                dfs2(i,adj,visited);
            }
        }
    }
	public:
	//Function to find number of strongly connected components in the graph.
    int kosaraju(int V, vector<vector<int>>& adj)
    {
        //code here
        vector<bool>visited(V,false);
        stack<int>st;
        for(int i=0;i<V;i++){
            if(!visited[i]){
                dfs(i,adj,visited,st);
            }
        }
        
        vector<vector<int>>adjT(V);
        
        for(int i=0;i<V;i++){
            // visited marked to false
            visited[i]=0;
            for(auto j:adj[i]){
                adjT[j].push_back(i);
            }
        }
        
        int ans=0;
        while(!st.empty()){
            int node=st.top();
            st.pop();
            if(!visited[node]){
                ans++;
                dfs2(node,adjT,visited);
            }
        }
        return ans;
    }
};
```
