---
description: 'https://leetcode.com/problems/find-mode-in-binary-search-tree/'
---

# 501. Find Mode in Binary Search Tree

## Analysis

Same elements are placed together in inorder traversal

## Code

### C++ 

```cpp
class Solution {
public:
    vector<int> vec;
    int maxCnt = 1;
    int curCnt = 0;
    int curNum = 0;
    
    void inorder(TreeNode* root){
        if (!root) return;
        
        inorder(root->left);
        
        
        if (root->val == curNum) curCnt++;
        else{
            curNum = root->val;
            curCnt = 1; 
        }
        if (curCnt > maxCnt){
            maxCnt = curCnt;
            vec.clear();
            vec.push_back(curNum);
        }
        else if (curCnt == maxCnt) vec.push_back(curNum);
        
        inorder(root->right);
        
        return;
    }
    
    vector<int> findMode(TreeNode* root) {
        inorder(root);
        return vec;
    }
};
```

