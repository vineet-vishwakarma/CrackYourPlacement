# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(nlogn)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution 
{
    public:
    //Function to find the minimum number of swaps required to sort the array. 
	int minSwaps(vector<int>&nums)
	{
	    // Code here
	    int n=nums.size();
	    int count=0;
      vector<pair<int,int>>v;
      
      for(int i=0;i<n;i++){
          v.push_back({nums[i],i});
      }
      sort(v.begin(),v.end());
      
      for(int i=0;i<n;i++){
          while(v[i].second!=i){
              count++;
              swap(v[i],v[v[i].second]);
          }
      }
      return count;
	}
};
```
