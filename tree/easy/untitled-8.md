---
description: 'https://leetcode-cn.com/problems/cousins-in-binary-tree/'
---

# 993. Cousins in Binary Tree

## Analysis



## Code

### C++ 

```cpp
class Solution {
public:
    int father = 0, depth = 0;

    bool helper(TreeNode* root, int x, int y, int curDepth, int curFather){
        if (!root) return 0;

        if(root->val == x || root->val == y){
            if (!father){
                depth = curDepth;
                father = curFather;
                return false;
            }
            else {
                return (depth == curDepth && father != curFather);
            }
        }

        return helper(root->left, x, y, curDepth+1, root->val) || 
                helper(root->right, x, y, curDepth+1, root->val);
    }

    bool isCousins(TreeNode* root, int x, int y) {
        return helper(root, x, y, 0, -1);
    }
};

class Solution {
public:
    int flag = 0;

    int getDepth(TreeNode* root, int val, int depth){
        if (!root) return 0;

        if ((root->left && root->left->val == val) || 
        (root->right && root->right->val == val)){
            flag += flag ? root->val : -root->val;
            return depth + 1;
        } 

        return getDepth(root->left, val, depth + 1) + getDepth(root->right, val, depth + 1);
    }

    bool isCousins(TreeNode* root, int x, int y) {
        int xDepth = getDepth(root, x, 0);
        int yDepth = getDepth(root, y, 0);

        return (xDepth == yDepth && flag);
    }
};
    
```



