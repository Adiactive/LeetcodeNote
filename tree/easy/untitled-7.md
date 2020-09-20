---
description: 'https://leetcode.com/problems/second-minimum-node-in-a-binary-tree/'
---

# 671. Second Minimum Node In a Binary Tree

## Analysis

不用拘泥于一步到位return最后结果，可以先存下来进行别的条件判断

## Code

### C++ 

```cpp
class Solution {
public: 
    int findSecondMinimumValue(TreeNode* root) {
        if (!root->left) return -1;
        
        int left = root->left->val, right = root->right->val;
        
        if (left == root->val) left =  findSecondMinimumValue(root->left);
        if (right == root->val) right =  findSecondMinimumValue(root->right);
        
        if (left == -1) return right;
        if (right == -1) return left;
        
        return min(left, right);
    }
};
```

