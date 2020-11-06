---
description: 'https://leetcode.com/problems/array-nesting/'
---

# 565. Array Nesting

## Analysis

Set visited elements to -1 to record the start of the loop.

## Code

### C++ 

```cpp
class Solution {
public:
    int arrayNesting(vector<int>& nums) {
        int maxLen = 1;
        int size = nums.size();
        
        for (int i = 0; i < size; i++){
            if (nums[i] >= 0){
                int cnt = 0, next = i;
                while(nums[next] >= 0){
                    int temp = next;
                    next = nums[next];
                    nums[temp] = -1;
                    cnt++;
                };
            
                maxLen = max(maxLen, cnt);
            }
        }
        
        return maxLen;
    }
};
```

