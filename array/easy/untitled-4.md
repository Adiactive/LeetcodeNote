---
description: 'https://leetcode-cn.com/problems/merge-sorted-array/'
---

# 88. Merge Sorted Array

## Analysis

Insert from the bottom to make sure no element would be overiden. 

## Code

### C++ 

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int p = m + n - 1, p1 = m -1, p2 = n - 1;

        while(p >= 0){
            if (p2 >= 0 && (p1 < 0 || nums1[p1] < nums2[p2])){
                nums1[p--] = nums2[p2--];
            }
            else{
                nums1[p--] = nums1[p1--];
            }
        }
    }
};
```

