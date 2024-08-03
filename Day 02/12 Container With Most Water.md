# Approach (Two Pointers)
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int maxArea(vector<int>& height) {
        int n=height.size();
        int i=0,j=n-1;
        int ans=0;
        int area=0;
        while(i<j){
            if(height[i]<height[j]){
                area=height[i]*(j-i);
                i++;
            }else{
                area=height[j]*(j-i);
                j--;
            }
            ans=max(area,ans);
        }
        return ans;
    }
};
```
