# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int leastInterval(vector<char>& tasks, int n) {
        int len=tasks.size();
        
        vector<int>alpha(26,0);
        
        for(int i=0;i<len;i++){
            alpha[tasks[i]-'A']++;
        }
        
        sort(alpha.begin(),alpha.end());
        
        int maxFreq=alpha[25];
        int noOfCharacterWithMaxFreq=0;
        
        for(int i:alpha){
            if(i==maxFreq){
                noOfCharacterWithMaxFreq++;
            }
        }
        int gaps = maxFreq-1;
        int gapsLen = n-(noOfCharacterWithMaxFreq-1);
        int emptySpace = gaps*gapsLen;
        int availableTask = len - maxFreq * noOfCharacterWithMaxFreq;
        int idles = max(0,emptySpace-availableTask);

        return len+idles;
    }
};
```
