# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(k)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        priority_queue<pair<int,int>>pq;
        vector<int>ans;
        for(int i=0;i<nums.size();i++){
            pq.push({nums[i],i});

            if(i>=(k-1)){
                while(i-pq.top().second>=k){
                    pq.pop();
                }
                ans.push_back(pq.top().first);
            }
        }  
        return ans;
    }
};
```
