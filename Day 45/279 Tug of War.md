# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(N*2<sup>N</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(2<sup>N</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution{
    public:
    int sum;
    int solve(vector<int>&arr,int index,int taken,int x,int currsum,int total){
        if(index>=arr.size())
            return INT_MAX;
        
        if(taken==x){
            return currsum;
        }
        
        int a=solve(arr,index+1,taken,x,currsum,total);
        int b=solve(arr,index+1,taken+1,x,currsum+arr[index],total);
        
        if(abs(total-a)<abs(total-b))
            return a;
            
        return b;
    }
    vector<vector<int>>minDifference(vector<int>& arr, int n){
        //Code here
        sum=accumulate(arr.begin(), arr.end(),0);
        int x=n/2;
        int ans=solve(arr,0,0,x,0,sum/2);
        
        return {{min(ans,sum-ans)},{max(ans,sum-ans)}};
    }
};
```
