# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int mctFromLeafValues(vector<int>& arr) {
        if(arr.size()==2)
            return arr[0]*arr[1];
        
        int res = 0;
        vector<int>stack={INT_MAX};
        for(int a:arr){
            while(stack.back()<=a){
                int mid=stack.back();
                stack.pop_back();
                res+=mid*min(stack.back(),a);
            }
            stack.push_back(a);
        }
        for(int i=2;i<stack.size();i++){
            res+=stack[i]*stack[i-1];
        }
        return res;
    }
};
```
