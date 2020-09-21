---
description: 'https://leetcode.com/problems/average-of-levels-in-binary-tree/'
---

# 637. Average of Levels in Binary Tree

## Analysis

1. 简单的BFS，不用存储节点数，每次开始加新的一层前队里有的结点数就是当前层的结点数
2. 声明不要int强转double，范围可能报错

## Code

### C++ 

```cpp
class Solution {
public:
    vector<double> averageOfLevels(TreeNode* root) {
        std::vector<double> avg;
        std::queue<TreeNode*> nodes;
        nodes.push(root);
        
        while(!nodes.empty()){
            double sum = 0;
            int size = nodes.size();
            for (int i = 0; i < size; i++){
                TreeNode* node = nodes.front();
                nodes.pop();
                sum += node->val;
                if (node->left) nodes.push(node->left);
                if (node->right) nodes.push(node->right);
            }

            avg.push_back(sum / size);
        }
        return avg;
    }
};
```

