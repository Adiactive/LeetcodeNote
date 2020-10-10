---
description: 'https://leetcode.com/problems/convert-bst-to-greater-tree/'
---

# 538. Convert BST to Greater Tree

## Analysis

Ez reversed Inorder, i.e. add the right child first

## Code

### C++ 

```cpp
class Solution {
public:
    int preSum = 0;
    
    void rvsInorder(TreeNode* root){
        if (!root) return;
        rvsInorder(root->right);
        
        root->val += preSum;
        preSum = root->val;
        
        rvsInorder(root->left);
        
        return;
    }
    
    TreeNode* convertBST(TreeNode* root) {
        rvsInorder(root);
        return root;
    }
};
```

