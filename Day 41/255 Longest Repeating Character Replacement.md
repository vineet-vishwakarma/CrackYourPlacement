# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int characterReplacement(string s, int k) {
        int n=s.length();
        int i=0;
        int j=0;
        int maxC=0;
        int ans=-1;
        unordered_map<char,int> mp;
        while(j<n){
            mp[s[j]]++;
            maxC=max(maxC,mp[s[j]]);
            
            int curr=j-i+1;
            if(curr-maxC>k) {
                mp[s[i]]--;
                i++;
            }
            curr=j-i+1;
            ans=max(ans,curr);
            j++;
        }
        
        return ans; 
    }
};
```