# Similar to Largest Rectangle in Histogram

# Approach 
<!-- Describe your approach to solving the problem. -->
- Find next smaller elements
- Find prev smaller elements
- Find number of ways of particular element
- Add it to sum

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<int> prevSmallerElement(vector<int>arr,int n){
        stack<int>s;
        vector<int>ans(n);
        for(int i=0;i<n;i++){
            while(!s.empty() && arr[s.top()]>arr[i]){
                s.pop();
            }
            ans[i]=s.empty()?-1:s.top();
            s.push(i);
        }
        return ans;
    }

    vector<int> nextSmallerElement(vector<int>arr,int n){
        stack<int>s;
        vector<int>ans(n);
        for(int i=n-1;i>=0;i--){
            while(!s.empty() && arr[s.top()]>=arr[i]){
                s.pop();
            }
            ans[i]=s.empty()?n:s.top();
            s.push(i);
        }
        return ans;
    }

    int sumSubarrayMins(vector<int>& arr) {
        int n=arr.size();

        vector<int>prev(n); 
        prev = prevSmallerElement(arr,n);

        vector<int>next(n); 
        next = nextSmallerElement(arr,n);

        long long sum=0;
        int mod=1000000007;

        for(int i=0;i<n;i++){
            long long d1=i-prev[i];
            long long d2=next[i]-i;

            long long totalWays=d1*d2;
            long long sumInTotalWays=arr[i]*totalWays;

            sum=(sum+sumInTotalWays)%mod;
        }
        return (int)sum;
    }
};
```
