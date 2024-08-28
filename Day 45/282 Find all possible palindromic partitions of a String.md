# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(N*2<sup>N</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(N<sup>2</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
  public:
    bool f(int i,int j,string &s){
        if(i>=j)
            return true;
        if(s[i]!=s[j])
            return false;
        return f(i+1,j-1,s);
        
    }
    
    
    bool isPalindrome(string &s){
        int i=0;
        int j=s.size()-1;
        
        return f(i,j,s);
        
    }
    
    void recur(int i,string &s,vector<vector<string>> &ans,vector<string> &p){
        if(i>=s.size()){
            ans.push_back(p);
            return;
        }
        string t="";
        for(int k=i;k<s.size();k++){
            t+=s[k];
            if(isPalindrome(t)){
                p.push_back(t);
                recur(k+1,s,ans,p);
                p.pop_back();
                
            }
        }
        return;
    }
    vector<vector<string>> allPalindromicPerms(string S) {
        // code here
        vector<vector<string>>ans;
        vector<string>p;
    
        recur(0,S,ans,p);
        return ans;
    }
};
```
