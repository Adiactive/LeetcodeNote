---
description: 'https://leetcode.com/problems/odd-even-linked-list/'
---

# 328. Odd Even Linked List

## Analysis

Stupid problem

## Code

### C++

```cpp
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        if (!head || !head->next) return head;
        
        ListNode* odd = head, *even = head->next, *evenHead = even;
        ListNode* cur = even->next;
        bool isOdd = true;
        
        while(even && even->next){
            odd->next = even->next;
            even->next = even->next->next;
            odd = odd->next;
            even = even->next;
        }
        
        odd->next = evenHead;
        return head;
    }
};
```

