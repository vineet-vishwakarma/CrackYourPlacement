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