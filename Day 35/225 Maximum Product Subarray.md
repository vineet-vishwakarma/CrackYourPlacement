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
    int maxProduct(vector<int>& nums) {
        int n=nums.size();
        int r=nums[0];
        long long int imax=r,imin=r;
        for(int i=1;i<n;i++){
            if (nums[i]<0)
                swap(imax,imin);
            imax=imax*nums[i]>nums[i]?imax*nums[i]:nums[i];
            imin=imin*nums[i]<nums[i]?imin*nums[i]:nums[i];

            r=imax>r?imax:r;
        }
        return r;
    }
};
```
