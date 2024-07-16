# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n) only for recursive sorting
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    long long findMinDiff(vector<long long> a, long long n, long long m){
        //code
        int i=0,j=m-1;
        sort(a.begin(),a.end());
        long long ans=INT_MAX;
        while(i<n && j<n){
            ans=min(ans,(a[j]-a[i]));
            i++;
            j++;
        }
        return ans;
    }   
};
```
