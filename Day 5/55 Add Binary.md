# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    string addBinary(string a, string b) {
        if(b.size()>a.size()) 
            swap(a,b);
        
        while(b.size()<a.size()) 
            b.insert(b.begin(),'0');
        
        int carry=0;
        string ans="";

        for(int i=b.size()-1;i>=0;i--){        
            if(b[i]=='1' && a[i]=='1'){
                if(carry==0) 
                    ans.insert(ans.begin(),'0');
                else 
                    ans.insert(ans.begin(),'1');
                carry = 1;
            }else if(b[i]=='0' && a[i]=='0'){
                if(carry==0) 
                    ans.insert(ans.begin(),'0');
                else
                    ans.insert(ans.begin(),'1');
                carry=0;
            }else if((b[i]=='0' && a[i]=='1') || (b[i]=='1' && a[i] == '0')){
                if(carry == 0) 
                    ans.insert(ans.begin(),'1');   
                else 
                    ans.insert(ans.begin(),'0');
            }
        }
        if(carry==1) 
            ans.insert(ans.begin(),'1');

        return ans;
    }
};
```
