# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int minCost(string colors, vector<int>& neededTime) {
        int totalTime=0; 
        int i=0,j=0;

        while(i<neededTime.size() && j<neededTime.size()){
            int currTotal=0,currMax=0;

            while(j<neededTime.size() && colors[i]==colors[j]){
                currTotal+=neededTime[j];
                currMax=max(currMax,neededTime[j]); 
                j++;
            }
            totalTime+=currTotal-currMax; 
            i=j; 
        }
        return totalTime; 
    }
};
```
