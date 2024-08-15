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
    vector<int> topKFrequent(vector<int>& nums, int k) {
        unordered_map<int,int>mp;
        vector<int>ans;

        for(int i=0;i<nums.size();i++)
        {
            mp[nums[i]]++;
        }

        vector<pair<int,int>>v(mp.begin(),mp.end());
        sort(v.begin(),v.end(),[](const auto& a, const auto& b){
            return a.second > b.second; 
        });

        for(auto i: v)
        {
            ans.push_back(i.first);
            k--;
            if(k==0)
                return ans;
            
        }
        return {};
    }
};
```
