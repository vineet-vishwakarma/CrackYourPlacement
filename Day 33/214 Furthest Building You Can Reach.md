# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogl) where l=ladders
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(l)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int furthestBuilding(vector<int>& heights,int bricks,int ladders){
        int n=heights.size();
        priority_queue<int,vector<int>,greater<int>>pq;
        for(int i=0;i<n-1;i++){
            int diff=heights[i+1]-heights[i];
            if(diff>0){
                if(pq.size()<ladders){
                    pq.push(diff);
                }else{
                    if(pq.empty() || pq.top()>=diff){
                        bricks-=diff;
                    }else{
                        int curr=pq.top(); 
                        pq.pop();
                        pq.push(diff);
                        bricks-=curr;
                    }
                    if(bricks<0) 
                        return i;
                }
            }
        }
        return n-1;
    }
};
```
