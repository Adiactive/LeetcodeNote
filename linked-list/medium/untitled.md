---
description: 'https://leetcode.com/problems/split-linked-list-in-parts/'
---

# 725. Split Linked List in Parts

## Analysis

Stupid problem

## Code

### C++

```cpp
class Solution {
public:
    vector<ListNode*> splitListToParts(ListNode* root, int k) {
        ListNode *head = root;
        int cnt = 0;
        
        while(head){
            cnt++;
            head = head->next;
        }
        
        int num = cnt / k, rem = cnt % k;
        
        vector<ListNode*> res;
        
        for(int i = 0; i < k; i++){
            res.push_back(root);
            for(int j = 0; j < num + (i < rem ? 1 : 0) - 1; j++)
                root = root->next;
            
            if (root){
                ListNode *pre = root;
                root = root->next;
                pre->next = nullptr;
            }
        }

        return res;
    }
};
```

