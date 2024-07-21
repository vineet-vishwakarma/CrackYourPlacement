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
    bool isPossible(vector<int>v,int n,int k,int mid)
    {
        int cow = 1;
        int lastPos = v[0];
        for(int i=0;i<n;i++){
            if(v[i]-lastPos>=mid){
                cow++;
                if(cow==k)
                    return true;
                lastPos=v[i];
            }
        }
        return false;
    }
    int solve(int n, int k, vector<int> &stalls) {
        // Write your code here
        sort(stalls.begin(),stalls.end());
        int ans=-1;
        int maxi=INT_MIN;
        
        for(int i=0;i<n;i++){
            maxi=max(maxi,stalls[i]);
        }
        
        int s=0;
        int e=maxi;
        while(s<=e){
            int mid = s+(e-s)/2;
            if(isPossible(stalls,n,k,mid)){
                ans=mid;
                s=mid+1;
            }
            else
                e=mid-1;
        }
        return ans;
    }
};
```
