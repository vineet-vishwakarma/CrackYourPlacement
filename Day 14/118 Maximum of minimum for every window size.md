# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution
{
    public:
    //Function to find maximum of minimums of every window size.
    vector<int> prevSmallerElement(int arr[],int n){
        stack<int>s;
        vector<int>ans(n);
        for(int i=0;i<n;i++){
            while(!s.empty() && arr[s.top()]>arr[i]){
                s.pop();
            }
            ans[i]=s.empty()?-1:s.top();
            s.push(i);
        }
        return ans;
    }

    vector<int> nextSmallerElement(int arr[],int n){
        stack<int>s;
        vector<int>ans(n);
        for(int i=n-1;i>=0;i--){
            while(!s.empty() && arr[s.top()]>=arr[i]){
                s.pop();
            }
            ans[i]=s.empty()?n:s.top();
            s.push(i);
        }
        return ans;
    }
    
    vector<int>maxOfMin(int arr[], int n)
    {
        // Your code here
        vector<int>prev(n); 
        prev = prevSmallerElement(arr,n);
        
        vector<int>next(n); 
        next = nextSmallerElement(arr,n);
        
        vector<int>ans(n+1,0);
        
        for(int i=0;i<n;i++){
            int len=next[i]-prev[i]-1;
            ans[len]=max(ans[len],arr[i]);
        }
        for(int i=n-1;i>=0;i--){
            ans[i]=max(ans[i],ans[i+1]);
        }
        
        ans.erase(ans.begin());
        return ans;
    }
};
```
