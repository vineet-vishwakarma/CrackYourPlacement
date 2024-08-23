# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int uniquePaths(int m, int n) {
        vector<int>pre(n,1);
        vector<int>cur(n,1);

        for(int i=1;i<m;i++){
            for (int j=1;j<n;j++){
                cur[j]=pre[j]+cur[j-1];
            }
            swap(pre,cur);
        }
        return pre[n-1];
    }
};
```
