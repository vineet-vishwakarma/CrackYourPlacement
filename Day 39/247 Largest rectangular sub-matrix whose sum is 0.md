# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(N*M<sup>2</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(N*M<sup>2</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```cpp []
class Solution{
  public:
  vector<vector<int>> sumZeroMatrix(vector<vector<int>> a){
      //Code Here
        int m = a.size(), n = a[0].size();
        int max_area = 0, up = -1, down = -1, left = -1, right = -1;
        vector<vector<int>> ps(m, vector<int>(n));
    
        for (int i = 0; i < m; i++) {
            ps[i][0] = a[i][0];
            for (int j = 1; j < n; j++)
                ps[i][j] = ps[i][j - 1] + a[i][j];
        }
    
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <= i; j++) {
                vector<int> tmp(m);
                unordered_map<int, int> mp{{0, -1}};
    
                for (int k = 0; k < m; k++)
                    tmp[k] = ps[k][i] - ps[k][j] + a[k][j];
    
                int s = 0, pos_s = -1, pos_e = -1;
    
                for (int l = 0; l < m; l++) {
                    s += tmp[l];
                    if (mp.count(s)) {
                        if (pos_e == -1 || (l - mp[s]) > (pos_e - pos_s + 1))
                            pos_s = mp[s] + 1, pos_e = l;
                    } else {
                        mp[s] = l;
                    }
                }
    
                if (pos_s != -1) {
                    int area = (pos_e - pos_s + 1) * (i - j + 1);
                    if (area > max_area || (area == max_area && (j < left || (j == left && pos_e < up && down < pos_e)))) {
                        up = pos_s, down = pos_e, left = j, right = i, max_area = area;
                    }
                }
            }
        }
        
       if(max_area == 0) return {{}};
       
       vector<vector<int>> ans(down-up+1, vector<int>(right-left+1));
       for(int i = up; i <= down; i++)
          for(int j = left; j <= right; j++) 
             ans[i-up][j-left] = a[i][j];
       return ans;
  }
};
```
