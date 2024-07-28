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
    string removeDuplicates(string s, int k) {
        
        int n=s.size();
        if(n<k)
            return s;

        string ans="";
        stack<pair<char,int>>st;

        for(auto ch:s){
            if(st.empty() || st.top().first!=ch){
                st.push({ch,1});
            }else{
                auto top=st.top();
                st.push({ch,st.top().second+1});
                if(st.top().second==k){
                    int j=0;
                    while(j!=k){
                        st.pop();
                        j++;
                    }
                }
            }
        }

        while(!st.empty()){
            ans.push_back(st.top().first);
            st.pop();
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```
