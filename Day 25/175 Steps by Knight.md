# Complexity
- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(nn<sup>2</sup>)

# Code
```
class Solution 
{
    public:
    //Function to find out minimum steps Knight needs to reach target position
    bool isValid(int x,int y,int n,vector<vector<bool>>&visited){
        if(x>=0 && x<n && y>=0 && y<n && !visited[x][y]){
            return true;
        }
        return false;
    }
	int minStepToReachTarget(vector<int>&KnightPos,vector<int>&TargetPos,int n)
	{
	    // Code here
	    int tx=TargetPos[0]-1,ty=TargetPos[1]-1;
	    int kx=KnightPos[0]-1,ky=KnightPos[1]-1;
	    
	    if(tx==kx && ty==ky)
	        return 0;
	    
	    int ans=0;
	    
	    vector<vector<bool>>visited(n,vector<bool>(n,false));
	    vector<pair<int,int>>dirs={{1,2},{1,-2},{-1,2},{-1,-2},{2,1},{-2,1},{2,-1},{-2,-1}};
	    
	    queue<pair<int,int>>q;
	    q.push({kx,ky});
	    visited[kx][ky]=true;
	    
	    while(!q.empty()){
	        int s=q.size();
	        ans++;
	        
	        for(int i=0;i<s;i++){
	            auto curr=q.front();
	            q.pop();
	            
	            int x=curr.first;
	            int y=curr.second;
	            
	            for(auto dir:dirs){
	                int newX=x+dir.first;
	                int newY=y+dir.second;
	                
	                if(newX==tx && newY==ty)
	                    return ans;
	                
	                if(isValid(newX,newY,n,visited)){
	                    visited[newX][newY]=true;
	                    q.push({newX,newY});
	                }
	            }
	        }
	        
	    }
	    return ans;
	}
};
```
