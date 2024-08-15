# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*l+|A|<sup>2</sup>)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(|A|+k)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Node{
    public:
    Node*children[26];
    bool isTerminal;
    Node(){
        for(int i=0;i<26;i++){
          children[i]=NULL;
        }
        isTerminal=false;
    }
};

class Trie{
    public:
    Node*root;
    Trie(){
        root=new Node();
    }
    
    void insert(string &str){
        Node*curr=root;
        for(int i=0;i<str.size();i++){
            int index = str[i]-'a';
            if(curr->children[index]==NULL){
                curr->children[index] = new Node();
            }
            curr=curr->children[index];
        }
        curr->isTerminal = true;
    }
    
    bool solve(string str,int start){
        if(start>=str.size())
            return true;
        
        Node*curr=root;
        bool ans=0;
        
        for(int i=start;i<str.size();i++){
            int index=str[i]-'a';
            
            if(curr->children[index]==NULL)
                return false;
            else{
                curr=curr->children[index];
                if(curr->isTerminal){
                   if(solve(str,i+1))
                    return true;
                }
            }
        }
        return false;
    }
};

class Solution{
    public:
    // A : given string to search
    // B : vector of available strings
    
    int wordBreak(string A,vector<string>&B){
        //code here
        Trie trie;
        for(int i=0;i<B.size();i++){
            trie.insert(B[i]);
        }
        
        return trie.solve(A,0);
    }
};
```
