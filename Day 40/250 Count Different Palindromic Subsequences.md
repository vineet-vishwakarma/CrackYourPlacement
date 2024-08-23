# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution {
public:
    int countPalindromicSubsequences(string s) {
        int mod=1000000007;
        int n=s.size();
        int ans = 0;
        vector<map<char,int>>cnt(n),cnt1(n),cnt2(n);
        
        for(int L=1;L<=n;L++,cnt2=cnt1,cnt1=cnt)
            for(int i=0;i+L<=n;i++)
                for(char c:"abcd")
                    if (L==1){
                        cnt[i][c]=(s[i] == c);
                    } 
                    else if(s[i]!= c){
                        cnt[i][c] = cnt1[i+1][c];
                    } 
                    else if(s[i+L-1] != c){
                        cnt[i][c] = cnt1[i][c];
                    } 
                    else{
                        cnt[i][c] = 2;
                        for (char cc : "abcd") (cnt[i][c] += cnt2[i+1][cc]) %= mod;
                    }                    

        for(char c:"abcd"){
            (ans += cnt[0][c]) %= mod;
        }
        return ans;
    }
};
```