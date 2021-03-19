---
description: 'https://leetcode-cn.com/problems/sort-colors/'
---

# 75. Sort Colors

## Analysis

Double pointer, zero pointer from start, two pointer from end, and traverse the array. Notice here after swapping current element with two pointer, we have to make sure the current element after swapping is not two before moving i backward, or this 2 will be skipped if there is no 0 in the rest of the elements.

Add a i != two in while loop to avoid index error after self-swapping. \(e.g. \[2\]\)

## Code

### C++ 

```cpp
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int zero = 0, two = nums.size() - 1;
        for(int i = 0; i <= two; i++){
            while(i != two && nums[i] == 2 )
                swap(nums[i], nums[two--]);
            if(nums[i] == 0)
                swap(nums[i], nums[zero++]);
        }
    }
};
```

