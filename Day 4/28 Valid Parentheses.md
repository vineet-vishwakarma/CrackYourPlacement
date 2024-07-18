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
    bool isValid(string s) {
        if(s[0]==')' || s[0]=='}' || s[0]==']')
            return false;

        stack<char>st;
        int n=s.size();

        for(int i=0;i<n;i++){
            if(s[i]=='(' || s[i]=='{' || s[i]=='['){
                st.push(s[i]);
            }else if(st.empty()){
                return false;
            }else{
                if(st.top()=='(' && s[i]==')'){
                    st.pop();
                }
                else if(st.top()=='{'&& s[i]=='}'){
                    st.pop();
                }
                else if(st.top()=='['&& s[i]==']'){
                    st.pop();
                }else{
                    st.push(s[i]);
                }
            }
        }
        return st.empty();
    }
};
```
