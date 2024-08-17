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
    int minRefuelStops(int target, int startFuel, vector<vector<int>>& stations) {
        int idx=0,stock = 0,ans=0;
        priority_queue<int> pq;
        pq.push(startFuel);
        while(!pq.empty()){
            int currFuel=pq.top();
            pq.pop();
            stock+=currFuel;
            if(stock >= target)
                return ans;
            while(idx < stations.size() and stock >= stations[idx][0]){
                pq.push(stations[idx][1]);
                idx++;
            }
            ans++;
        }
        return -1;
    }
};
```
