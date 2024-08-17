# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(k)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        priority_queue<int>pq; int n = matrix.size();
        for(int i = 0; i < n; i++)
            for(int j = 0; j < n; j++){
                pq.push(matrix[i][j]);
                if(pq.size() > k) pq.pop();
            }
        return pq.top();
    }
};
```
