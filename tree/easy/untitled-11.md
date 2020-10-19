---
description: 'https://leetcode.com/problems/two-sum-iv-input-is-a-bst/'
---

# 653. Two Sum IV - Input is a BST

## Analysis

Refer to [1. Two Sum](../../array/easy/1.-two-sum.md). Can also use inorder traversal to store all the elements and use double pointer \(i = 0, j = size  - 1\)

## Code

### C++ 

```cpp
class Solution {
public:
    std::set<int> set;
    
    bool findTarget(TreeNode* root, int k) {
        if (!root) return false;
        
        if (set.count(k - root->val)) return true;
        else set.insert(root->val);
        
        return findTarget(root->left, k) || findTarget(root->right, k);123456
    }
};
```

