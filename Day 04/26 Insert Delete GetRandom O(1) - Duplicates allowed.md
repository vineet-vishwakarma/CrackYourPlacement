# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(1)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class RandomizedCollection {
public:
    vector<int> v;
    unordered_map<int, unordered_set<int>> map;
    RandomizedCollection() {
        
    }
    
    bool insert(int val) {
        v.push_back(val);
        map[val].insert(v.size()-1);
        
        return map[val].size()<=1;
    }
    
    bool remove(int val) {
        if(map[val].size()==0) 
            return false;
        
        int ind= *map[val].begin();
        map[val].erase(ind);
        
        int num=v.back();
        swap(v[ind], v[v.size()-1]);
        map[num].insert(ind);
        map[num].erase(v.size()-1);
        v.pop_back();
        return true;
    }
    
    int getRandom() {
        return v[rand()%v.size()];
    }
};

```
