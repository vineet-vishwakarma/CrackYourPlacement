# Complexity
- Time Complexity: O(V+E)
- Space Complexity: O(V+E)

# Code
```
class Solution{
public:
    // Function to determine if graph can be coloured with at most M colours such
    // that no two adjacent vertices of graph are coloured with same colour.
    bool isSafe(int &u, int &c, int n, bool graph[101][101], vector<int> &color){
        for(int i=0;i<n;i++){
            if(u!=i && graph[u][i] && color[i]==c){
                return false;
            }
        }
        return true;
        
    }
    bool solve(int curr,bool graph[101][101],vector<int>&color,int m,int n){
        if(curr==n) 
            return true;
        
        // Try all colors to curr
        for(int i=0;i<m;i++){
            if(isSafe(curr,i,n,graph,color)){
                color[curr]=i;
                if(solve(curr+1,graph,color,m,n))
                   return true;
                // Backtrack
                color[curr]=-1;
            }
        }
        
        return false;
        
    }
    bool graphColoring(bool graph[101][101], int m, int n) {
        // your code here
        vector<int>color(n,-1);
        return solve(0,graph,color,m,n);
    }
};
```
