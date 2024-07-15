# Approach $$(Dutch National Flag Algorithm)$$
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int n=nums.size();
        int s=0,mid=0,e=n-1;

        while(mid<=e){
            if(nums[mid]==0){
                swap(nums[mid],nums[s]);
                s++;
                mid++;
            }else if(nums[mid]==1){
                mid++;
            }else{
                swap(nums[mid],nums[e]);
                e--;
            }
        }
    }
};
```