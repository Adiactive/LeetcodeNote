---
description: 'https://leetcode.com/problems/path-sum/'
---

# 112. Path Sum

## Analysis

傻逼题目

## Code

### C++ 

```cpp
class Solution {
public:
    bool hasPathSum(TreeNode* root, int sum) {
        if (root == NULL) return false;

        sum -= root->val;
        if (root->left == NULL && root->right == NULL && sum == 0) return true;
        
        return (hasPathSum(root->left, sum) || hasPathSum(root->right, sum));
    }
};
```

