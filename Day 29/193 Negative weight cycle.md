# Approach (Prim's Algorithm)

# Complexity
- Time Complexity: O(n*m)
- Space Complexity: O(n)

# Code
```
class Solution {
  public:
	int isNegativeWeightCycle(int n, vector<vector<int>>edges){
	    // Code here
        vector<int> dist(n, 1e9);
        int source = 0;
        dist[source] = 0;
        for(int j=0; j<n-1; j++){
            for(int i=0; i<edges.size(); i++){
                int u = edges[i][0];
                int v = edges[i][1];
                int w = edges[i][2];
                
                if(dist[u] + w < dist[v]){
                    dist[v] = dist[u] + w;
                }
           }
        }
        
        for(int i=0; i < edges.size(); i++){
            int u = edges[i][0];
            int v = edges[i][1];
            int w = edges[i][2];
            
            if(dist[u] != 1e9 && dist[u] + w < dist[v]){
                return 1;
            }
        }
        return 0;
	}
};
```
