# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n<sup>2</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n<sup>2</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int findTheCity(int n, vector<vector<int>>& edges, int distanceThreshold) {
        vector<vector<pair<int,int>>>adj(n);

        for(auto i:edges){
            adj[i[0]].push_back({i[1],i[2]});
            adj[i[1]].push_back({i[0],i[2]});
        }
        
        vector<vector<int>>dist(n,vector<int>(n,INT_MAX));
        queue<pair<int,int>>q;

        for(int i=0;i<n;i++){
            q.push({i,0});
            while(!q.empty()){
                auto front=q.front();
                q.pop();
                
                for(auto it:adj[front.first]){
                    if(i==it.first){
                        continue;
                    }

                    if(it.second+front.second<=distanceThreshold && it.second+front.second<=dist[i][it.first]){
                        if(it.second<=distanceThreshold && it.second<dist[front.first][it.first]){
                            dist[front.first][it.first]=it.second;
                            dist[it.first][front.first]=it.second;
                        }
                        dist[i][it.first]=it.second+front.second;
                        q.push({it.first,it.second+front.second});
                        dist[it.first][i]=it.second+front.second;
                    }
                }
            }
        }

        int f=0,maxi=INT_MAX,ans=0;

        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(dist[i][j]!=INT_MAX)
                    f++;
            }
            if(maxi>=f){
                maxi=f;
                ans=i;
            }
            f=0;
        }
        return ans;
    }
};
```
