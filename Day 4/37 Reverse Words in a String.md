# Approach
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
    string reverseWords(string s) {
        int i=0;
        int n=s.length();
        string ans="";
        while(i<n){
            string temp="";
            if(i==n)
                break;
            while(i<n && s[i]==' ')
                i++;

            while(i<n && s[i]!=' '){
                temp.push_back(s[i]);
                i++;
            }
            reverse(temp.begin(),temp.end());
            temp.push_back(' ');
            ans+=temp;
            temp.clear();
        }
        i=ans.size()-1;
        while(ans[i]==' '){
            ans.pop_back();
            i--;
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```
