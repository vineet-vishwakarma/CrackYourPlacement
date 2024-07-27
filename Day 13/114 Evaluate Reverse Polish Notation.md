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
    int operate(int a,int b,string i){
        if(i=="+"){
            return a+b;
        }
        else if(i=="-"){
            return a-b;
        }
        else if(i=="*"){
            return a*b;
        }
        else if(i=="/"){
            return a/b;
        }
        else{
            return 0;
        }
    }
    int evalRPN(vector<string>& tokens) {
        stack<string>st;
        int n=tokens.size();

        for(auto i:tokens){
            if(i=="+"||i=="-"||i=="/"||i=="*"){
                int a=stoi(st.top());
                st.pop();

                int b=stoi(st.top());
                st.pop();

                string res=to_string(operate(b,a,i));
                st.push(res);
            }else{
                st.push(i);
            }
        }
        return stoi(st.top());
    }
};
```
