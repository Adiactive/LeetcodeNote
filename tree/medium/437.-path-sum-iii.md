---
description: 'https://leetcode.com/problems/path-sum-iii/'
---

# 437. Path Sum III

## Analysis

傻逼题目，注意return边界，可能满足条件之后还能多次满足，不急着return

## Code

### C++ 

```cpp
class Solution {
public:    
    int pathSumHelper(TreeNode* root, int sum){
        if (root == NULL) return 0;
        int isNewPath = 0;
        if (sum == root->val) isNewPath = 1;
        
        return isNewPath + pathSumHelper(root->left, sum-root->val) + pathSumHelper(root->right, sum-root->val);
    }
    
    int pathSum(TreeNode* root, int sum) {
        if (root == NULL) return 0;        
        
        return pathSumHelper(root, sum) + pathSum(root->left, sum) + pathSum(root->right, sum);
    }
};
```

