# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(1)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Node
{
public:
    int key;
    int val;
    Node*next;
    Node*prev;
    Node(int key,int val)
    {
        this->val=val;
        this->key=key;
    }
};

class LRUCache {
public:
    
    Node*head=new Node(-1,-1);
    Node*tail=new Node(-1,-1);

    int size;
    unordered_map<int,Node*>mp;
    
    LRUCache(int capacity) {
        size=capacity;
        head->next=tail;
        tail->prev=head;
    }

    void insertNode(Node* newNode){
        Node*temp=head->next;
        
        newNode->next=temp;
        newNode->prev=head;

        head->next=newNode;
        temp->prev=newNode;
    }

    void deleteNode(Node* delNode){
        Node*prev=delNode->prev;
        Node*next=delNode->next;

        prev->next=next;
        next->prev=prev;
    }
    
    int get(int key) {
        if(mp.contains(key)){
            Node*curr=mp[key];
            int ans=curr->val;
            mp.erase(key);
            deleteNode(curr);
            insertNode(curr);

            mp[key]=head->next;
            return ans;
        }
        return -1;
    }
    
    void put(int key, int value) {
        if(mp.contains(key)){
            Node*curr=mp[key];
            mp.erase(key);
            deleteNode(curr);
        }

        if(mp.size()==size){
            mp.erase(tail->prev->key);
            deleteNode(tail->prev);
        }

        Node*newNode=new Node(key,value);
        
        insertNode(newNode);
        mp[key]=head->next;
    }
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache* obj = new LRUCache(capacity);
 * int param_1 = obj->get(key);
 * obj->put(key,value);
 */
```