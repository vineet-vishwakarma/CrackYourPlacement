# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int maxi=0,mini=INT_MAX;
        int i=0;
        while(i<prices.size()){
            mini=min(mini,prices[i]);
            if(prices[i]>=mini){
                maxi=max(maxi,prices[i]-mini);
            }
            i++;
        }
        return maxi;
    }
};
```
