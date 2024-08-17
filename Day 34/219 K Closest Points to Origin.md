# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogk)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(k)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<vector<int>> kClosest(vector<vector<int>>& points, int k) {
        vector<vector<int>>ans(k);
        priority_queue<vector<int>>pq;
        for (auto p:points){
            int x=p[0],y=p[1];
            pq.push({x*x+y*y,x,y});
            if (pq.size()>k){
                pq.pop();
            }
        }
        
        for(int i=0;i<k;i++){
            auto top=pq.top();
            pq.pop();
            ans[i]={top[1], top[2]};
        }
        return ans;
    }
};
```
