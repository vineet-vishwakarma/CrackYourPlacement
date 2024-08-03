# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class solution {
  public:
    long long multiplyTwoLists(Node *first, Node *second) {
        // code here
        // int mod=10e9+7;
        long long n1=0,n2=0;
        
        while(first){
            n1=(n1*10+first->data)%1000000007;
            first=first->next;
        }
        
        while(second){
            n2=(n2*10+second->data)%1000000007;
            second=second->next;
        }
        return (n1*n2)%1000000007;
    }
};
```
