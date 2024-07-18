# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int findMaxValueOfEquation(vector<vector<int>>& points, int k) {
        priority_queue<pair<int,int>>p;
        int n=points.size();
        int ans=INT_MIN;
        for(int i=0;i<n;i++){
            while(!p.empty() && points[i][0]-p.top().second>k){
                p.pop();
            }
            if(!p.empty()){
                ans=max(ans,points[i][0]+points[i][1]+p.top().first);
            }
            p.push({points[i][1]-points[i][0],points[i][0]});
        }
        return ans;
    }
};
```