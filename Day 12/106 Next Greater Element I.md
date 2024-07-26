# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        stack<int>st;

        int n=nums2.size();
        vector<int>v(n);
        st.push(-1);
        
        for(int i=n-1;i>=0;i--){
            while(st.top()!=-1 && nums2[st.top()]<nums2[i]){
                st.pop();
            }
            v[i]=st.top()==-1?-1:nums2[st.top()];
            st.push(i);
        }
        for(auto i:v) cout<<i<<" ";
        vector<int>ans(nums1.size());
        for(int i=0;i<nums1.size();i++){
            for(int j=0;j<n;j++){
                if(nums1[i]==nums2[j]){
                    ans[i]=v[j];
                }
            }
        }
        return ans;
    }
};
```
