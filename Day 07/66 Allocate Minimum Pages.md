# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public:
    bool isPossible(int arr[], int n, int m,int mid)
    {
        int student=1;
        int pg=0;
        
        for(int i=0;i<n;i++){
            if(pg +arr[i]<=mid){
                pg+=arr[i];
            }
            else{
                student++;
                if(student>m || arr[i]>mid){
                    return false;
                }
                pg=arr[i];
            }
        }
        return true;
    }
    // Function to find minimum number of pages.
    long long findPages(int n, int arr[], int m) {
        // code here
        if(m>n)
            return -1;
            
        int sum=0,ans=-1;
        
        for(int i=0;i<n;i++){
            sum+=arr[i];
        }
        
        int s=0,e=sum;
        
        while(s<=e){   
            int mid=s+(e-s)/2;
            
            if(isPossible(arr,n,m,mid)){
                ans=mid;
                e=mid-1;
            }
            else{
                s=mid+1;
            }
        }
        return ans;
    }
};
```
