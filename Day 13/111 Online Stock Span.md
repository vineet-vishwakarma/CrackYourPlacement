# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class StockSpanner {
public:
    vector<int>v;
    StockSpanner() {
        
    }
    
    int next(int price) {
        v.push_back(price);
        int ans=0;
        for(int i=v.size()-1;i>=0;i--){
            if(v[v.size()-1]>=v[i]){
                ans++;
            }else{
                break;
            }
        }
        return ans;
    }
};

/**
 * Your StockSpanner object will be instantiated and called as such:
 * StockSpanner* obj = new StockSpanner();
 * int param_1 = obj->next(price);
 */
```
