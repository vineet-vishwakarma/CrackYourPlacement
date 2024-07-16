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
    int maxProfit(vector<int>& prices) {
        int profit=0;

        for(int i=1;i<prices.size();i++){
            if(prices[i]>prices[i-1]){
                profit+=(prices[i]-prices[i-1]);
            }
        }
        return profit;
    }
};
```
