# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

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
    int trap(vector<int>& height) {
        int n=height.size();
        int l=0,r=n-1;
        int lMax=0,rMax=0;
        int ans=0;
        
        while(l<r){
            if(height[l]>lMax){
                lMax=height[l];
            }
            if(height[r]>rMax){
                rMax=height[r];
            }

            if(lMax<rMax){
                ans+=lMax-height[l];
                l++;
            }else{
                ans+=rMax-height[r];
                r--;
            }
        }

        return ans;
    }
};
```
