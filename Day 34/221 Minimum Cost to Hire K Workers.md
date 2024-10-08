# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(k)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    double mincostToHireWorkers(vector<int>& quality, vector<int>& wage, int k) {
        int n=quality.size();
        double sum=0, result=INT_MAX;
        vector<pair<double,int>> details;
        for(int i=0;i<n;i++){
            details.push_back({wage[i]/(double)quality[i],quality[i]});
        }
        sort(details.begin(), details.end());
        priority_queue<int> pq;
        for(int i=0;i<n;i++){
            pq.push(details[i].second);
            sum+=details[i].second;
            if(pq.size()>k){
                sum-=pq.top();
                pq.pop();
            }
            if(pq.size()==k){
                result=min(result,sum*details[i].first);
            }
        }
        return result;
    }
};
```
