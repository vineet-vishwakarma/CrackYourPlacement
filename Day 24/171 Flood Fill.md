# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int start;
    int n,m;
    void dfs(vector<vector<int>>& image, int sr, int sc, int color){
        if(sr<0 || sr>=n || sc<0 || sc>=m || image[sr][sc]!=start || image[sr][sc]==color)
            return;
        
        image[sr][sc]=color;
        
        dfs(image,sr-1,sc,color);
        dfs(image,sr,sc+1,color);
        dfs(image,sr,sc-1,color);
        dfs(image,sr+1,sc,color);
    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        n=image.size();
        m=image[0].size();

        start=image[sr][sc];
        dfs(image,sr,sc,color);
        return image;
    }
};
```
