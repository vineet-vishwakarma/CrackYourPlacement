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
    int maxScore(vector<int>& cardPoints, int k) {
        int sum=0;
        int n=cardPoints.size();
        for(int i=0;i<k;i++){
            sum+=cardPoints[i];
        }
        int curr=sum;
        for(int i=0;i<k;i++){
            curr=curr-cardPoints[k-1-i]+cardPoints[n-i-1];
            sum=max(sum,curr);
        }
        return sum;
    }
};
```
