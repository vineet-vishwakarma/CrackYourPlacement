# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public:
    int findPair(int n, int x, vector<int> &arr) {
        // code here
        sort(arr.begin(),arr.end());
        int i=0,j=1;
        while(i<n && j<n){
            int diff=abs(arr[i]-arr[j]);
            
            if(i!=j && diff==x)
                return 1;
            else if(diff>x){
                i++;
            }else{
                j++;
            }
        }
        return -1;
    }
};
```