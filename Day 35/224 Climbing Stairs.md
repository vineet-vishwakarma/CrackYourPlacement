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
    int climbStairs(int n) {
        if(n==0 || n==1 || n==2)
            return n;

        int next=1,prev=0,sum=0;
        
        while(n--){
            sum=(next+prev);
            prev=next;
            next=sum;
        }
        return sum;
    }
};
```