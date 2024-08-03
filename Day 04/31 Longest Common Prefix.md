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
    string longestCommonPrefix(vector<string>& strs) {
        string ans="";
        sort(strs.begin(),strs.end());
        string first=strs.front();
        string last=strs.back();

        for(int i=0;i<first.size();i++){
            if(first[i]!=last[i])
                return ans;
            ans.push_back(first[i]);
        }
        return ans;
    }
};
```
