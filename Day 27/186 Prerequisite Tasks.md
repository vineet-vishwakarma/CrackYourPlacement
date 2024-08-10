# Complexity
- Time Complexity: O(N+P)
- Space Complexity: O(N+P)

# Code
```
class Solution {
public:
	bool isPossible(int N,int P, vector<pair<int, int> >& prerequisites) {
	    // Code here
        vector<int>adj[N];
        vector<int>InDeg(N,0);
        
        for(int i=0;i<P;i++){
            adj[prerequisites[i].second].push_back(prerequisites[i].first);
            InDeg[prerequisites[i].first]++;
        }
        queue<int>q;
        for(int i=0;i<N;i++){
            if(!InDeg[i])
            q.push(i);
        }
        int count = 0;
        while(!q.empty()){
            int curr=q.front();
            q.pop();
            count++;
            for(int j=0;j<adj[curr].size();j++){
                InDeg[adj[curr][j]]--;
                
                if(InDeg[adj[curr][j]]==0){
                    q.push(adj[curr][j]);
                }
            }
        }
        return count==N?1:0;
	}
};
```
