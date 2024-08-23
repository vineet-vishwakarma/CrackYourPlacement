# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution 
{
    public:
    //Function to find the maximum profit and the number of jobs done.
    vector<int> JobScheduling(Job arr[], int n) 
    { 
        // your code here
        int max_dead=1;
        for(int i=0;i<n;i++){
            max_dead=max(max_dead,arr[i].dead);
        }
        
        sort(arr,arr+n,[](Job& j1, Job&j2){
           return j1.profit > j2.profit; 
        });
        
        vector<bool>deads(max_dead+1,0);
        int totalProfit=0, totalJob=0;
        
        for(int i=0; i<n; i++){
            for(int j=arr[i].dead; j>0; j--){
                if(!deads[j]){
                    deads[j]=1;
                    totalProfit+=arr[i].profit;
                    totalJob++;
                    break;
                }
            }
            if(totalJob==max_dead) 
                break;
        }
        
        return {totalJob, totalProfit};
    } 
};
```
