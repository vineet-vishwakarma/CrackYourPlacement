# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(m)

# Code
```
/*You are required to complete this method*/

class Solution{
  public:
      vector<int>nextSmallerElement(vector<int>arr,int n){
        vector<int>ans(n);
        stack<int>s;
        s.push(-1);

        for(int i=n-1;i>=0;i--){
            while(s.top()!=-1 && arr[s.top()]>=arr[i]){
                s.pop();
            }

            ans[i]=s.top();
            s.push(i);
        }
        return ans;
    }
    vector<int>prevSmallerElement(vector<int>arr,int n){
        vector<int>ans(n);
        stack<int>s;
        s.push(-1);

        for(int i=0;i<n;i++){
            while(s.top()!=-1 && arr[s.top()]>=arr[i]){
                s.pop();
            }

            ans[i]=s.top();
            s.push(i);
        }
        return ans;
    }
    
    int largestRectangleArea(vector<int>heights){
        int n=heights.size();

        vector<int>next(n);
        vector<int>prev(n);

        next=nextSmallerElement(heights,n);
        prev=prevSmallerElement(heights,n);
        int area = INT_MIN;
        for(int i=0;i<n;i++){
            int l=heights[i];
            if(next[i]==-1){
                next[i]=n;
            }
            int b=next[i]-prev[i]-1;

            int newArea = l*b;
            area = max(area,newArea);
        }
        return area;
    }
    
    int maxArea(int matrix[MAX][MAX], int n, int m) {
        // Your code here
        
        int ans = INT_MIN; 
        vector<int>heights(m,0);
        
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(matrix[i][j]==1){
                    heights[j]++;
                }else{
                    heights[j]=0;
                }
            }
            ans=max(ans,largestRectangleArea(heights));
        }
        return ans;
    }
};
```
