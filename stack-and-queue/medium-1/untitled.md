---
description: 'https://leetcode-cn.com/problems/sort-of-stacks-lcci/'
---

# 面试题 03.05. Sort of Stacks LCCI

## Analysis

s1 : main stack, desc order

s2: sub stack, asc order

![](../../.gitbook/assets/image%20%2815%29.png)

## Code

### C++ 

```cpp
class SortedStack {
private:
    stack<int> s1;
    stack<int> s2;  
public:
    SortedStack() {

    }
    
    void push(int val) {
        while(!s1.empty() && s1.top() < val){
            s2.push(s1.top());
            s1.pop();
        }

        while(!s2.empty() && s2.top() > val){
            s1.push(s2.top());
            s2.pop();
        }
        s1.push(val);
    }
    
    void pop() {
        while(!s2.empty()){
            s1.push(s2.top());
            s2.pop();
        };
        if (!s1.empty()) s1.pop();
    }
    
    int peek() {
        while(!s2.empty()){
            s1.push(s2.top());
            s2.pop();
        };
        return !s1.empty() ? s1.top() : -1;
    }
    
    bool isEmpty() {
        return s1.empty() && s2.empty();
    }
};




class SortedStack {
private:
    stack<int> s;

public:
    SortedStack() {

    }
    
    void push(int val) {
        stack<int> temp;

        while(!s.empty() && s.top() < val){
            temp.push(s.top());
            s.pop();
        }

        s.push(val);

        while(!temp.empty()){
            s.push(temp.top());
            temp.pop();
        }
    }
    
    void pop() {
        if (!s.empty()) s.pop();
    }
    
    int peek() {
        if (s.empty()) return -1;
        return s.top();
    }
    
    bool isEmpty() {
        return s.empty();
    }
};

/**
 * Your SortedStack object will be instantiated and called as such:
 * SortedStack* obj = new SortedStack();
 * obj->push(val);
 * obj->pop();
 * int param_3 = obj->peek();
 * bool param_4 = obj->isEmpty();
 */
```

