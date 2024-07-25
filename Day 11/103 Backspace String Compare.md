# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

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
    string remove(string s){
        stack<char>st;
        int n=s.size();
        string ans="";

        for(int i=0;i<n;i++){
            if(s[i]!='#'){
                st.push(s[i]);
            }else{
                if(!st.empty())
                    st.pop();
            }
        }
        while(!st.empty()){
            ans.push_back(st.top());
            st.pop();
        }
        return ans;
    }
    bool backspaceCompare(string s, string t) {
        return remove(s)==remove(t);
    }
};
```
