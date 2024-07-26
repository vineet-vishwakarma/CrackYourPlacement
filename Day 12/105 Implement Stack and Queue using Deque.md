# Code
```
#include <bits/stdc++.h>
using namespace std;

class MyQueue {
public:
    deque<int>d;
    MyQueue() {
        
    }
    
    void push(int x) {
        d.push_back(x);
    }
    
    int pop() {
        int ans=d.front();
        d.pop_front();
        return ans;
    }
    
    int peek() {
        return d.front();
    }
    
    bool empty() {
        return d.empty();
    }
};
class MyStack {
public:
    deque<int>d;
    MyStack() {
        
    }
    
    void push(int x) {
        d.push_front(x);
    }
    
    int pop() {
        int ans=d.front();
        d.pop_front();
        return ans;
    }
    
    int top() {
        return d.front();
    }
    
    bool empty() {
        return d.empty();
    }
};

int main()
{
    MyStack st;
    st.push(10);
    st.push(20);
    st.push(30);
    
    while(!st.empty()){
        cout<<st.top()<<" ";
        st.pop();
    }
    cout<<endl;
    
    MyQueue q;
    q.push(10);
    q.push(20);
    q.push(30);
    
    while(!q.empty()){
        cout<<q.peek()<<" ";
        q.pop();
    }

    return 0;
}
```
