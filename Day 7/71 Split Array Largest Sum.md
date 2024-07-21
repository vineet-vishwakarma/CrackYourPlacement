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
    bool isPossible(vector<int>& a,int mid, int n, int m)
    {
        int sc=1;
        long long sum=0;
        for(int i=0;i<n;i++){
            if(sum+a[i]>mid){
                sc++;
                sum=a[i];
                if(sc>m || a[i]>mid) 
                    return false;
            }else{
                sum+=a[i];
            }
            
        }
        return true;
    }
    int splitArray(vector<int>& nums, int k) {
        int n=nums.size();
        int sum=0;
        for(int i=0;i<n;++i){
            sum+=nums[i];
        }
        int s=0,e=sum;
        int ans=-1;
        while(s<=e){
            int mid=s+(e-s)/2;
            if(isPossible(nums,mid,n,k)){
                ans=mid;
                e=mid-1;
            }else{
                s=mid+1;
            }
        }
        return ans;
    }
};
```
