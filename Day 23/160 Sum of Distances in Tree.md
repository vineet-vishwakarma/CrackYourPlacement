# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<vector<int>>v;
    vector<int>counter,res;
        
    void dfs(int i,int p=-1){
        for(auto u:v[i]){
            if(u==p) 
                continue;
            
            dfs(u,i);
            counter[i]+=counter[u];
            res[i]+=res[u]+counter[u];
        }
        counter[i]+=1;
    }

    void dfs2(int i,int n,int p=-1){
        for(auto u:v[i]){
            if(u==p) 
                continue;
            
            res[u]=res[i]-counter[u]+n-counter[u];
            dfs2(u,n,i);
        }
    }
    
    vector<int> sumOfDistancesInTree(int n, vector<vector<int>>& edges) {
        v.resize(n);

        for(int i=0;i<n-1;i++){
            v[edges[i][0]].push_back(edges[i][1]);
            v[edges[i][1]].push_back(edges[i][0]);
        }

        res.resize(n);
        counter.resize(n);

        dfs(0);
        dfs2(0,n);
        return res;
    }
};
```
