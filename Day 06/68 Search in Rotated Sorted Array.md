# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(logn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int s=0,e=nums.size()-1;

        while(s<=e){
            int mid=(s+e)/2;

            if(nums[mid]==target){
                return mid;
            }else if(nums[s]<=nums[mid]){
                if(target>=nums[s] && target<=nums[mid]){
                    e=mid-1;
                }else{
                    s=mid+1;
                }
            }else{
                if(target>=nums[mid] && target<=nums[e]){
                    s=mid+1;
                }else{
                    e=mid-1;
                }
            }
        }
        return -1;
    }
};
```
