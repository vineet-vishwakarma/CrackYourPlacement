# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: 
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution
{
    public:
    //Function to find the largest number after k swaps.
    void solve(string str,int k,int ind,string& maxi){
        
        maxi=max(maxi,str);
        
        if(k==0) 
            return; 
        
        int n=str.size();
        
        for(int i=ind;i<n-1;i++){
            for (int j=i+1;j<n;j++){
                if(str[i]<str[j]){
                    swap(str[i],str[j]);
                    solve(str,k-1,i+1,maxi);
                    swap(str[i],str[j]);
                }
            }
        }
        
    }
    string findMaximumNum(string str, int k)
    {
       // code here.
       string maxi="";
       solve(str,k,0,maxi);
       return maxi;
    }
};
```
