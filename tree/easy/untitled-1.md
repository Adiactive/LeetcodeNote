---
description: 'https://leetcode.com/problems/sum-of-left-leaves/'
---

# 404. Sum of Left Leaves

## Analysis

注意有一边没有孩子的情况

## Code

### C++ 

```cpp
class Solution {
public:
    int sumOfLeftLeaves(TreeNode* root) {
        if (root == NULL || root->left == NULL && root->right == NULL) return 0;
        int val = 0;
        if (root->left && root->left->left == NULL && root->left->right == NULL) val = root->left->val;
        return val + sumOfLeftLeaves(root->left) + sumOfLeftLeaves(root->right);
    }
};
```

