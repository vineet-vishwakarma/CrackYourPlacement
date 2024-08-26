# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n!)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    bool seen[16]={};
    int ans=0;

    int dfs(int n,int pos=1){
        if(pos>n) 
            return ans++;
        for(int i=1;i<=n;i++){
            if(!seen[i] && (i%pos==0 || pos%i==0)){
                // marking i as seen
                seen[i]=true;
                dfs(n,pos+1);
                // backtracking
                seen[i]=false;
            }
        }
        return ans;
    }
    int countArrangement(int n) {
        if(n<4) 
            return n;
        return dfs(n);
    }
};
```
