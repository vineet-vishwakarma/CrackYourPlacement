# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

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
    bool canCross(vector<int>& stones) {
        unordered_map<int,unordered_set<int>>mp;    
        mp[stones[0]+1]={1};

        for(int i=1;i<stones.size();i++){      
            int position=stones[i];

            for(auto it:mp[position]){           
                mp[position+it].insert(it);      
                mp[position+it+1].insert(it+1);
                mp[position+it-1].insert(it-1);
            }
        }
        return mp[stones.back()].size()!=0;  
    }
};
```
