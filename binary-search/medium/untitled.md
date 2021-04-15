---
description: 'https://leetcode-cn.com/problems/single-element-in-a-sorted-array/'
---

# 540. Single Element in a Sorted Array

## Analysis

Bitwise operation

## Code

### C++ 

```cpp
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int res = nums[0], len = nums.size();

        for(int i = 1; i < len; i++)
            res ^= nums[i];

        return res;
    }
};
```

