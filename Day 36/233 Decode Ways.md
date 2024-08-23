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
    int numDecodings(string s) {
        if(s.empty() || s[0]=='0'){
            return 0;
        }

        int n=s.size();
        vector<int>dp(n+1,0);
        dp[0]=1;
        dp[1]=1;

        for(int i=2;i<=n;i++){
            int oneDigit=s[i-1]-'0';
            int twoDigits=stoi(s.substr(i-2,2));

            if(oneDigit!=0){
                dp[i]+=dp[i-1];
            }

            if(10<=twoDigits && twoDigits<=26){
                dp[i]+=dp[i-2];
            }
        }

        return dp[n];
    }
};
```
