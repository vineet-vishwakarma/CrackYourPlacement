# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public:
    // Function to find if there is a celebrity in the party or not.
    int celebrity(vector<vector<int> >& arr, int n) {
        // code here
        int top=0,down=n-1;
        
        while(top<down){
            if(arr[top][down]==1 && arr[down][top]==0){
                top++;
            }else if(arr[top][down]==0 && arr[down][top]==1){
                down--;
            }else{
                top++;
                down--;
            }
            
            if(top>down){
                return -1;
            }
        }
        
        for(int i=0;i<n;i++){
            if(i==top){
                continue;
            }
            if(arr[top][i]==1){
                return -1;
            }else if(arr[i][top]==0){
                return -1;
            }
        }
        
        return top;
    }
};
```
