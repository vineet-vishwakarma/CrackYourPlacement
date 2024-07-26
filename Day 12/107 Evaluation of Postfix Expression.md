# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution
{
    public:
    //Function to evaluate a postfix expression.
    int operate(int a,int b,char ch){
        if(ch=='+'){
            return a+b;
        }
        else if(ch=='-'){
            return a-b;
        }
        else if(ch=='*'){
            return a*b;
        }
        else if(ch=='/'){
            return a/b;
        }
        else{
            return 0;
        }
    }
    int evaluatePostfix(string S)
    {
        // Your code here
        stack<int>st;
        for(char ch:S){
            if(ch=='+'||ch=='-'||ch=='/'||ch=='*'){
                int a=st.top();
                st.pop();
                int b=st.top();
                st.pop();
                int res=operate(b,a,ch);
                st.push(res);
            }else{
                st.push(ch-'0');
            }
        }
        return st.top();
    }
};
```
