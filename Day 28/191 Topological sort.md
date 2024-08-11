# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(V+E)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(V)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution
{
	public:
	//Function to return list containing vertices in Topological order. 
	vector<int> topoSort(int V, vector<int> adj[]) 
	{
	    // code here
	    vector<int>res;
	    vector<int>indegree(V,0);
	    
	    for(int i=0;i<V;i++){
	        for(int n:adj[i]){
	            indegree[n]++;
	        }
	    }
	    
	    queue<int>q;
	    for(int i=0;i<V;i++){
	        if(indegree[i]==0){
	            q.push(i);
	        }
	    }
	    
	    while(!q.empty()){
	        int curr=q.front(); 
	        q.pop();
	        res.push_back(curr);
	        
	        for(int i:adj[curr]){
	            indegree[i]--;
	            if(indegree[i]==0) 
	                q.push(i);
	        }
	    }
	    return res;
	}
};
```
