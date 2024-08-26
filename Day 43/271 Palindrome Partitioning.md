# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(2<sup>n</sup>*n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(2<sup>n</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    bool isPalindrome(string s,int i,int j){
        while(i<=j){
            if(s[i]!=s[j])
                return false;
            i++;
            j--;
        }
        return true;
    }
    void recur(string s,int idx, vector<string>sub,vector<vector<string>>&ans){
        if(idx==s.length()){
            ans.push_back(sub);
            return;
        }
        
        for(int i=idx;i<s.length();i++){
            if(isPalindrome(s,idx,i)){
                sub.push_back(s.substr(idx,i-idx+1));
                recur(s,i+1,sub,ans);
                sub.pop_back();
            }
        }
    }
    vector<vector<string>> partition(string s) {
        vector<vector<string>>ans;
        vector<string>sub;
        recur(s,0,sub,ans);
        return ans;
    }
};
```
