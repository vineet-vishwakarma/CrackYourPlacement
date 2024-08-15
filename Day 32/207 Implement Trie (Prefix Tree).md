# Approach
<!-- Describe your approach to solving the problem. -->

# Complexityo
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*len of words)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class TrieNode{
public:
    TrieNode*children[26];
    bool terminal;
};
class Trie {
public:
    TrieNode*root;
    Trie() {
        root=new TrieNode();
    }
    
    void insert(string word) {
        TrieNode*child=root;
        for(char ch:word){
            int i=ch-'a';
            if(child->children[i]==NULL) 
                child->children[i]=new TrieNode();
            child=child->children[i];
        }
        child->terminal=true;
    }
    
    bool search(string word) {
        TrieNode* node = root;
        for(char ch:word){
            int i=ch-'a';
            if(node->children[i]==NULL) 
                return false;
            node=node->children[i];
        }
        return node->terminal;
    }
    
    bool startsWith(string prefix) {
        TrieNode*node=root;
        for(char ch:prefix){
            int i=ch-'a';
            if(node->children[i]==NULL) 
                return false;
            node=node->children[i];
        }
        return true;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */
```
