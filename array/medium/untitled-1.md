---
description: 'https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/'
---

# 378. Kth Smallest Element in a Sorted Matrix

## Analysis

O\(log\(max - min\) \* n\): Binary search, find the number of elements less than _mid =_ \(lo + hi\) / 2 which divide the whole matrix into 2 parts: \[lo, mid\], \[mid + 1, hi\].

Correctness: mid will never be equal to hi due to the equation _mid =_ \(lo + hi\) / 2. Refer to [comment](https://leetcode-cn.com/problems/kth-smallest-element-in-a-sorted-matrix/solution/you-xu-ju-zhen-zhong-di-kxiao-de-yuan-su-by-leetco/472018) and [solution](https://leetcode-cn.com/problems/kth-smallest-element-in-a-sorted-matrix/solution/you-xu-ju-zhen-zhong-di-kxiao-de-yuan-su-by-leetco/).

## Code

### C++ 

```cpp
class Solution {
public:
    bool helper(vector<vector<int>>& matrix, int n, int mid, int k){
        int r = n - 1, c = 0;
        int count = 0;
        
        while (r >= 0 && c < n){
            if (matrix[r][c] <= mid){
                count += r + 1;
                c++;
            }
            else r--;
        }
        
        return count < k;
    }
    
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        int n = matrix.size();
        int lo = matrix[0][0], hi = matrix[n - 1][n - 1];
        
        while(lo < hi){
            int mid = (hi + lo) >> 1;
            
            if (helper(matrix, n, mid, k)) lo = mid + 1;
            else hi = mid;
        }
        
        return hi;
    }
};
```

