---
description: 'https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/'
---

# 109. Convert Sorted List to Binary Search Tree

## Analysis

1. Convert to [Prob 108](108.-convert-sorted-array-to-binary-search-tree.md) \(vector/list\). （nlogn\)
2. Fast/slow pointer. \(nlogn\)
3. Inorder filling, the linked list is ordered the same as inorder traversal of BST. \(n\)

## Code

### C++ 

```cpp
class Solution {
public:
    TreeNode* helper(ListNode* head, int size){
        if (!size) return NULL;
        
        int index = size / 2;
        ListNode* cur = head;
        while (index--) cur = cur->next;
        
        TreeNode* root = new TreeNode(cur->val);
        root->left = helper(head, size / 2);
        root->right = helper(cur->next, (size - 1) / 2);
        
        return root;
    }
    
    TreeNode* sortedListToBST(ListNode* head) {
        int size = 0;
        ListNode* cur = head;
        while (cur){
            size++;
            cur = cur->next;
        }
        TreeNode* root = helper(head, size);
        return root;
    }
};
```



```cpp
class Solution {
public:
    TreeNode* helper(ListNode*& head, int start, int end){
        if (start > end) return NULL;
        
        int index = (start + end) / 2;
        TreeNode* root = new TreeNode();
        
        root->left = helper(head, start, index - 1);        
        root->val = head->val;
        head = head->next;
        root->right = helper(head, index + 1, end);
        
        return root;
    }
    
    TreeNode* sortedListToBST(ListNode* head) {
        int size = 0;
        ListNode* cur = head;
        while (cur){
            size++;
            cur = cur->next;
        }
        TreeNode* root = helper(head, 0, size - 1);
        return root;
    }
};
```

