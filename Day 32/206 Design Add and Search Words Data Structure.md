# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(26<sup>n</sup>)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class TrieNode{
    public:
        TrieNode*children[26];
        bool isLeaf;

        TrieNode(){
            for(int i=0;i<26;i++){
                children[i]=NULL;
            }
            isLeaf=false;
        }
};
class WordDictionary {
public:
    TrieNode*root;
    WordDictionary() {
        root=new TrieNode();
    }
    
    void insertSolve(TrieNode*root,string word){
        if(word.size()==0){
            root->isLeaf=true;
            return;
        }

        int index=word[0]-'a';
        TrieNode*child;

        if(root->children[index]!=NULL){
            child=root->children[index];
        }else{
            child=new TrieNode();
            root->children[index]=child;
        }

        insertSolve(child,word.substr(1));
    }
    void addWord(string word) {
        insertSolve(root,word);
    }
    
    bool pathSearch(string word, TrieNode* root, int index){
        if(index==word.size()) 
            return root->isLeaf; 

        TrieNode*node=root;
        char c=word[index];
        int idx=c-'a';

        if(c=='.'){ 
            for(int i=0;i<26;i++){
                if(node->children[i]){
                    if(pathSearch(word,node->children[i],index+1)) 
                        return true;
                }
            }
            return false;
        }else{
            if(node->children[idx]==NULL)
                return false;
            return pathSearch(word,node->children[idx],index+1); 
        }
    }
    bool search(string word) {
        return pathSearch(word,root,0);
    }
};

/**
 * Your WordDictionary object will be instantiated and called as such:
 * WordDictionary* obj = new WordDictionary();
 * obj->addWord(word);
 * bool param_2 = obj->search(word);
 */
```