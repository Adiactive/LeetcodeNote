---
description: 'https://leetcode.com/problems/subtree-of-another-tree/'
---

# 572. Subtree of Another Tree

## Analysis

你好好看看题，注意边界。判断syntex和semantic是否都需要递归

## Code

### C++ 

```cpp
class Solution {
public:
    bool isSubtreeHelper(TreeNode* s, TreeNode* t){
        if (t == NULL && s == NULL) return true;
        if (t != NULL && s != NULL && (t->val == s->val)) return (isSubtreeHelper(s->left, t->left) && isSubtreeHelper(s->right, t->right));
        return false;
    }
    
    bool isSubtree(TreeNode* s, TreeNode* t) {
        if (s == NULL) return false;
        return isSubtreeHelper(s, t) ? true : (isSubtree(s->left, t) || isSubtree(s->right, t));
    }
};
```

