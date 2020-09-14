---
description: 'https://leetcode.com/problems/longest-univalue-path/'
---

# 687. Longest Univalue Path

## Analysis

1. 在函数中计算**通过**该root的path的长度，更新全局变量，然后返回左右递归的最大值交由上一个节点继续计算
2. 不要拘泥递归return最后答案，可以用全局变量更新来取最值，这样不用判断下层递归传上来的值可能的各种情况，比如这道如果用递归就需要考虑下层传上来的maxlength是通过了子节点还是未通过。

## Code

### C++ 

```cpp
class Solution {
public:
    int max_path = 0;
    
    int depth(TreeNode* root){
        if (root == NULL) return 0;
        
        int left = 0;
        int right = 0;
        
        int left_depth = depth(root->left);
        int right_depth = depth(root->right);
        
        if (root->left && root->left->val == root->val) left = left_depth + 1;
        if (root->right && root->right->val == root->val) right = right_depth + 1;
        
        this->max_path = max(left + right, this->max_path);
        
        return max(left, right);
    }
    
    int longestUnivaluePath(TreeNode* root) {
        depth(root);
        return this->max_path;
    }
};
```

