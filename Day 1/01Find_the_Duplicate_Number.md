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

# Approach 2 (Slow and Fast Pointers)

# Complexity
- Time complexity: O(n)

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int n=nums.size();
        int j=1;
        for(int i=1;i<n;i++){
            if(nums[i]!=nums[i-1]){
                nums[j]=nums[i];
                j++;
            }
        }
        return j;
    }
};
```