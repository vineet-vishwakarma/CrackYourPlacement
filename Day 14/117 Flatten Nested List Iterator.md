 Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: 
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * class NestedInteger {
 *   public:
 *     // Return true if this NestedInteger holds a single integer, rather than a nested list.
 *     bool isInteger() const;
 *
 *     // Return the single integer that this NestedInteger holds, if it holds a single integer
 *     // The result is undefined if this NestedInteger holds a nested list
 *     int getInteger() const;
 *
 *     // Return the nested list that this NestedInteger holds, if it holds a nested list
 *     // The result is undefined if this NestedInteger holds a single integer
 *     const vector<NestedInteger> &getList() const;
 * };
 */

class NestedIterator {
    vector<int>flattened;
    int index;

    vector<int>flatten(vector<NestedInteger> &nested){
        vector<int>ans;
        for(auto i:nested){
            if(i.isInteger()){
                ans.push_back(i.getInteger());
            }else{
                auto subList=flatten(i.getList());
                for(auto i:subList){
                    ans.push_back(i);
                }
                // ans.insert(ans.end(),subList.begin(),subList.end());
            }
        }
        return ans;
    }
public: 
    NestedIterator(vector<NestedInteger> &nestedList) {
        flattened=flatten(nestedList);
        index=0;
    }
    
    int next() {
        return flattened[index++];
    }
    
    bool hasNext() {
        return index<flattened.size();
    }
};

/**
 * Your NestedIterator object will be instantiated and called as such:
 * NestedIterator i(nestedList);
 * while (i.hasNext()) cout << i.next();
 */
```
