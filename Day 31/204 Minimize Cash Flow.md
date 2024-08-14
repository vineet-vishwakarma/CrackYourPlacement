# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public:
    int findMin(vector<int>&amount,int n){
        int min=1e9;
        int mini=-1;
        for(int i=0;i<n;i++){
            if(amount[i]<min) {
                min=amount[i];
                mini=i;
            }
        }
        return mini;
    }
    int findMax(vector<int> &amount,int n){
        int max=-1e9;
        int maxi=-1;
        for(int i=0;i<n;i++){
            if(amount[i]>max) {
                max=amount[i];
                maxi=i;
            }
        }
        return maxi;
    }
    void solve(vector<int> &amount,int n,vector<vector<int>> &ans){
        int mini=findMin(amount,n),maxi=findMax(amount,n);
        
        if(amount[mini]==0 && amount[maxi]==0) 
            return;
            
        int a=min(-amount[mini],amount[maxi]);
        
        amount[mini]+=a;
        amount[maxi]-=a;
        ans[mini][maxi]+=a;
        
        solve(amount,n,ans);
    }
    vector<vector<int>>minCashFlow(vector<vector<int>>&transaction,int n){
        // code here
        vector<vector<int>>ans(n,vector<int>(n,0));
        vector<int> amount(n,0);
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                amount[i]=amount[i]+transaction[j][i]-transaction[i][j];
            }
        }
        solve(amount,n,ans);
        return ans;
    }
};
```
