# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    string removeKdigits(string num, int k) {
        int n=num.size();
        if(n==k)
            return "0";

        string ans="";

        stack<char>st;
        for(int i=0;i<n;i++){
            while(!st.empty() && k>0 && num[i]<st.top()){
                st.pop();
                k--;
            }
            st.push(num[i]);
        }

        while(!st.empty()){
            if(k>0){
                st.pop();
                k--;
            }else{
                string ss(1,st.top());
                ans.insert(0,ss);
                st.pop();
            }
        }

        int i=0;
        while(ans[i]=='0'){
            i++;
        }
        ans.erase(0,i);
        if(ans.empty()){
            return "0";
        }

        return ans;
    }
};
```
