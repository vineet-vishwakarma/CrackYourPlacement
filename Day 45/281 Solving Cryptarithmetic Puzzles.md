# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(N)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(N)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution{
    public:
    const int mod = 1000000007,N = 100000,p=31;
    int p_pow[100000],h[100001];
    Solution(){
        p_pow[0] = 1;
        for(int i=1;i<N;i++)
            p_pow[i] = (1LL*p_pow[i-1]*p)%mod;
    }
    void compute_hash(string s){
        for(int i=0;i<s.size();i++)
            h[i+1] = (h[i]+1LL*(s[i]-'a'+1)*p_pow[i])%mod;
    }
    string solve(string s){
        int n = s.size()/2;
        for(int i=n;i>0;--i){
            int left_half_hash = h[i];
            int right_half_hash = (h[2*i]-h[i]+mod)%mod;
            if((1LL*left_half_hash*p_pow[i])%mod==right_half_hash){
                string ans = solve(s.substr(0,i));
                ans+='*'+s.substr(2*i,s.size());
                return ans;
            }
        }
        return s;
    }
    string compress(string s)
    {
        compute_hash(s);
        return solve(s);
    }
};
```
