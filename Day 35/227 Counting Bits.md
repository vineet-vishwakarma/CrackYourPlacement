# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<int> countBits(int n) {
        vector<int>ans(n);
        ans.push_back(0);  // for n = 0
        if(n==0) 
            return ans;
        
        for (int i=1;i<=n;i++){
            if(i%2==0) 
                ans[i]=ans[i/2];
            else
                ans[i]=ans[i-1]+1;
        }
        return ans;
    }
};
```
