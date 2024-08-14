# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n<sup>4</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n<sup>3</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<vector<vector<int>>>dp;
    int solve(vector<int> &boxes, int i, int j, int count) {
        if(i>j) 
            return 0;
        
        if(dp[i][j][count]!=-1) 
            return dp[i][j][count];
        
        int i0=i;
        int count0=count;
        
        while(i+1<=j && boxes[i]==boxes[i+1]){
            i++;
            count++;
        } 
            
        int ans=(count+1)*(count+1)+solve(boxes,i+1,j,0);
        
        for(int k=i+1;k<=j;k++){
            if(boxes[k]==boxes[i]){
                ans=max(ans,solve(boxes,i+1,k-1,0)+solve(boxes,k,j,count+1));
            }
        }
        return dp[i0][j][count0]=ans;
    }
    int removeBoxes(vector<int>& boxes) {
        int n=boxes.size();
        dp.resize(n+1, vector<vector<int>>(n+1, vector<int>(n+1, -1)));
        
        return solve(boxes, 0, n-1, 0);
    }
};
```
