# Approach (Moore's Voting Algorithm)
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
    int majorityElement(vector<int>& nums) {
        int count=0;
        int element;
        int n=nums.size();
        for(int i=0;i<n;i++){
            if(count==0)
                element=nums[i];
            
            if(element==nums[i]){
                count++;
            }else{
                count--;
            }
        }
        return element;
    }
};
```
