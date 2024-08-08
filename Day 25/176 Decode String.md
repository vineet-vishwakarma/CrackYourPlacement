# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(N * maxNumber*length of maxString)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(N * maxNumber*length of maxString)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    // recursive 
    string decode(string &s,int &i){
        string temp;
        while(i<s.size() && s[i]!=']'){
            if(!isdigit(s[i])){
                temp+=s[i];
                i++;
            }else{
                int n=0;
                while(i<s.size() && isdigit(s[i])){
                    n=n*10+s[i++]-'0';
                }

                i++;
                string t=decode(s,i);
                i++;

                while(n--){
                    temp+=t;
                }
            }
        }
        return temp;
    }

    string decodeString(string s) {
        stack<char>st;

        for(auto i:s){
            if(i!=']'){
                st.push(i);
            }else{
                string temp="";
                while(st.top()!='['){
                    temp=st.top()+temp;
                    st.pop();
                }
                st.pop();

                string k="";
                while(!st.empty() && isdigit(st.top())){
                    k=st.top()+k;
                    st.pop();
                }

                // cout<<temp<<" ";

                int n=stoi(k);
                // cout<<n<<" ";
                while(n--){
                    cout<<temp<<" ";
                    for(auto ch:temp){
                        st.push(ch);
                    }
                }
            }
        }

        string ans="";
        while(!st.empty()){
            ans=st.top()+ans;
            st.pop();
        }
        return ans;
    }
};
```
