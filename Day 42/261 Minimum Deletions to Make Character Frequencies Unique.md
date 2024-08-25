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
    int minDeletions(string s) {
        vector<int> freq(26, 0);

        for(char c:s){
            freq[c-'a']++; 
        }

        sort(freq.begin(),freq.end());
        int del=0;
        for(int i=24;i>=0;i--){
            if(freq[i]==0){
                break;
            }
            
            if(freq[i]>=freq[i+1]){
                int prev=freq[i];
                freq[i]=max(0,freq[i+1]-1);
                del+=prev-freq[i];
            }
        }
        return del;
    }
};
```