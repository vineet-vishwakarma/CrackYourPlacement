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
    bool canJump(vector<int>& nums) {
        int n=nums.size();
        int maxJump=0;
        if(n==1)
            return true;

        for(int i=0;i<n;i++){
            int jump=i+nums[i];
            if(i>maxJump)
                return false;
            maxJump=max(jump,maxJump);
            if(maxJump>=n-1){
                return true;
            }
        }
        return false;
    }
};
```
