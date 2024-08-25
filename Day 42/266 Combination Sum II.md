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
    int n;
    vector<int>curr;
    vector<vector<int>>ans;
    
    void solve(int target,int sum,vector<int>&candidates,int curInd){
        if(target==sum){
            ans.push_back(curr);
            return;
        }else if(sum>target){
            return;
        }
        
        for(int i=curInd;i<n;i++){
            if(i!=curInd && candidates[i]==candidates[i-1])
                continue;

            sum+=candidates[i];
            curr.push_back(candidates[i]);
            solve(target,sum,candidates,i+1);
            sum-=candidates[i];
            curr.pop_back();
        }
        
    }
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        n=candidates.size();
        sort(candidates.begin(), candidates.end());
        solve(target,0,candidates,0);
        return ans;
    }
};
```
