# Approach (Merge Sort)
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int merge(vector<int>& nums,int s,int mid,int e){
        int count=0;
        int j=mid+1;
        for(int i=s;i<=mid;i++){
            while(j<=e && nums[i]>(long)2*nums[j]){
                j++;
            }
            count+=(j-(mid+1));
        }
        vector<int>temp;
        int left=s,right=mid+1;

        while(left<=mid && right<=e){
            if(nums[left]<=nums[right]){
                temp.push_back(nums[left]);
                left++;
            }else{
                temp.push_back(nums[right]);
                right++;
            }
        }

        while(left<=mid){
            temp.push_back(nums[left]);
            left++;
        }
        while(right<=e){
            temp.push_back(nums[right]);
            right++;
        }

        for(int i=s;i<=e;i++){
            nums[i]=temp[i-s];
        }

        return count;
    }
    int mergeSort(vector<int>& nums,int s,int e){
        if(s>=e)
            return 0;
        int mid=(s+e)/2;
        int ans=mergeSort(nums,s,mid);
        ans+=mergeSort(nums,mid+1,e);
        ans+=merge(nums,s,mid,e);
        return ans;
    }
    int reversePairs(vector<int>& nums) {
        return mergeSort(nums,0,nums.size()-1);
    }
};
```
