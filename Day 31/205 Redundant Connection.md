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
    vector<int> parent;
    int find(int x){
        return parent[x]==x ? x : find(parent[x]);
    }
    vector<int> findRedundantConnection(vector<vector<int>>& edges) {
        int n=edges.size();
        if(n==0) 
            return{};
        parent.resize(n+1);
        for(int i=1;i<n+1;i++){
            parent[i]=i;
        }
        for(vector<int>edge:edges){
            int f1=find(edge[0]);
            int f2=find(edge[1]);
            if(f1!=f2)
                parent[f1]=f2;
            else
                return edge;
        }
        return {};
    }
};
```
