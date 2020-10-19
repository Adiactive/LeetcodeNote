---
description: 'https://leetcode.com/problems/minimum-absolute-difference-in-bst/'
---

# 530. Minimum Absolute Difference in BST

## Analysis

Ez inorder traversal. Initialize min when traversing second least value.

## Code

### C++ 

```cpp
class Solution {
public:
    int min = 0;
    int pre = -1;

    void inorder(TreeNode* root){
        if (!root) return;
        
        inorder(root->left);
        if ((root->val - pre < min) || (pre >= 0 && !min)) min = root->val - pre; 
        pre = root->val;
        inorder(root->right);
    }
    
    int getMinimumDifference(TreeNode* root) {
        inorder(root);
        return min;
    }
};
```

