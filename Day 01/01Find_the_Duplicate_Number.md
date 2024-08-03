# Find the Duplicate Number

# Approach 1 (Sorting)


# Complexity
- Time complexity: O(nlogn)

- Space complexity: O(n) only for recursive sorting

# Code
```
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int n=nums.size();
        sort(nums.begin(),nums.end());
        for(int i=1;i<n;i++){
            if(nums[i]==nums[i-1])
                return nums[i];
        }
        return -1;
    }
};

```

# Approach 2 (Slow and Fast Pointers)

# Complexity
- Time complexity: O(n)

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int slow=nums[0];
        int fast=nums[0];
        do{
            slow=nums[slow];
            fast=nums[nums[fast]];
        }while(slow!=fast);

        slow=nums[0];
        while(slow!=fast){
            slow=nums[slow];
            fast=nums[fast];
        }
        return slow;
    }
    
};
```
