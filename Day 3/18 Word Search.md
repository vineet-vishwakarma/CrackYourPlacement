# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*m*4<sup>l</sup>) where l is length of word
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(l)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int n;
    int m;
    bool dfs(vector<vector<char>>& board,int r,int c,int wordIndex, string word){
        if(wordIndex==word.size())
            return true;

        if(r<0 || c<0 || r>=n || c>=m){
            return false;
        }

        if(board[r][c]==' ' || board[r][c]!=word[wordIndex])
            return false;

        char ch = board[r][c];
        board[r][c]=' ';

        if( dfs(board,r-1,c,wordIndex+1,word) ||
            dfs(board,r,c+1,wordIndex+1,word) ||
            dfs(board,r+1,c,wordIndex+1,word) ||
            dfs(board,r,c-1,wordIndex+1,word))
            {
                return true;
            }

        board[r][c]=ch;
        return false;
    }
    bool exist(vector<vector<char>>& board, string word) {
        n=board.size();
        m=board[0].size();

        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(board[i][j]==word[0]){
                    if(dfs(board,i,j,0,word)){
                        return true;
                    }
                }
            }
        }
        return false;
    }
};
```
