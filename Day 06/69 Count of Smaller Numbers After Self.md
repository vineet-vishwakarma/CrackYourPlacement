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
    void merge(int s,int mid,int e,vector<int>& nums,vector<int>& count,vector<int>& index) {
        int n=e-s+1;
        vector<int>newIndex(n);
        int left=s,right=mid+1;
        int sortedPos=0,rightCount=0;

        while(left<=mid && right<=e){
            if(nums[index[right]]<nums[index[left]]){
                newIndex[sortedPos++]=index[right++];
                rightCount++;
            }else{
                count[index[left]]+=rightCount;
                newIndex[sortedPos++]=index[left++];
            }
        }

        while(left<=mid){
            count[index[left]]+=rightCount;
            newIndex[sortedPos++]=index[left++];
        }

        while(right<=e){
            newIndex[sortedPos++]=index[right++];
        }

        for(int i=0;i<n;i++){
            index[s+i]=newIndex[i];
        }
    }

    void mergeSort(int s,int e,vector<int>& nums,vector<int>& count,vector<int>& index){
        if(s>=e) 
            return;

        int mid=s+(e-s)/2;
        mergeSort(s,mid,nums,count,index);
        mergeSort(mid+1,e,nums,count,index);
        merge(s,mid,e,nums,count,index);
    }
    vector<int> countSmaller(vector<int>& nums) {
        int n=nums.size();
        vector<int>count(n,0);
        vector<int>index(n);

        for(int i=0;i<n;i++){
            index[i]=i;
        }

        mergeSort(0,n-1,nums,count,index);

        return count;
    }
};
```
