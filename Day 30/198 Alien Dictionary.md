# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*k+len)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(k)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution{
    public:
    string findOrder(string dict[], int N, int K) {
        //code here
        vector<int>InDeg(K,0);
        vector<int>adj[K];
        for(int i=0;i<N-1;i++){
           string str1=dict[i],str2=dict[i+1];
           int j=0,k=0;
           
            while(j<str1.size()&&k<str2.size()&&str1[j]==str2[k]){
                k++;
                j++;
            }
            if(j==str1.size())
                continue;
           
           adj[str1[j]-'a'].push_back(str2[k]-'a');
           InDeg[str2[k]-'a']++;
        }
        
        queue<int>q;
        for(int i=0;i<K;i++){
            if(!InDeg[i])
                q.push(i);
        }
        string ans;
        while(!q.empty()){
            int curr=q.front();
            q.pop();
            char c = 'a'+curr;
            ans+=c;
            for(int j=0;j<adj[curr].size();j++){
                InDeg[adj[curr][j]]--;
                if(InDeg[adj[curr][j]]==0)
                q.push(adj[curr][j]);
            }
        }
        return ans;
    }
};
```
