# Untitled

## Analysis

For recursion way, pass the new head all the way to the front using the return value and do nothing with it. Also, make sure the new tail points to null. Take into consideration a empty list.

## Code

### C++

```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode *pre = nullptr, *cur = head, *after;
        while(cur){
            after = cur->next;
            cur->next = pre;
            pre = cur;
            cur = after;
        }
        
        return pre;
    }
};

class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(!head || !head->next) return head;
        
        ListNode *newHead = reverseList(head->next);     
        
        head->next->next = head;
        head->next = nullptr;
        
        return newHead;
    }
};


```

