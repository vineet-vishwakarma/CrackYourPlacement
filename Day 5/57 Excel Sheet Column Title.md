# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(log<sub>26</sub>n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    string convertToTitle(int columnNumber) {
       string ans="";
        while(columnNumber>0){
            columnNumber--;
            int digit=columnNumber%26;
            columnNumber/=26;
            ans.push_back(digit+'A');
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```
