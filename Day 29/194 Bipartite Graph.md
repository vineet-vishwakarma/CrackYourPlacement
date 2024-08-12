# Approach (Prim's Algorithm)

# Complexity
- Time Complexity: O(v+e)
- Space Complexity: O(v)

# Code
```
class Solution {
  public:
    bool check(int node,int V,vector<int> adj[],vector<int> &color){
	    queue<int>q;
	    q.push(node);
        color[node]=0;
	    
	    while(!q.empty()){
	        int curr=q.front();
	        q.pop();	   
	        
	        for(auto i:adj[curr]){
	            if(color[i]==-1){
	                color[i]=!color[curr]; 
	                q.push(i);
	            }
	            else if(color[i]==color[curr]){
	                return false;
	            }
	        }
	    }
	    return true;        
    }
	bool isBipartite(int V, vector<int>adj[]){
	    // Code here
	    vector<int>color(V,-1);
	    for(int i=0;i<V;i++){
	        if(color[i]==-1){
	            if(!check(i,V,adj,color)){
	                return false;
	            }
	        }
	    }
	    return true;
	}
};
```
