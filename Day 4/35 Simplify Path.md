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
    string simplifyPath(string path) {
        stack<string>st;
        string temp,ans;
        int n=path.size();

        for(int i=0;i<n;i++){
            temp.clear();
            if(path[i]=='/')
                continue;
            while(i<n && path[i]!='/'){
                temp+=path[i];
                i++;
            }
            if(temp==".."){
                if(!st.empty())
                    st.pop();
            }
            else if(temp==".")
                continue;
            else
                st.push(temp);
        }
        while(!st.empty()){
            ans="/"+st.top()+ans;
            st.pop();
        }
        return ans.size()==0 ? "/" :ans;
    }
};
```
