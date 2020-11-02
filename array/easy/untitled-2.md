---
description: 'https://leetcode.com/problems/set-mismatch/'
---

# 645. Set Mismatch

## Analysis

Intuitively, we can use a map to store the traversed numbers, but it will result in O\(n\) in space complexity. To optimize it, we can further explore that the vector itself can be used as a map, for the numbers are supposed to be 1-n ----- exactly the index, or the 'key' of the map. That means when we traverse all the elements in the vector, all the index should be called once except the missing and duplicated index.

Thus, we can 'mark' the current element by reverse the value of nums\[i\]-th element in the vector, i.e. nums\[abs\(nums\[i\]-1\]. And when that value is already negative, we can know that the current element is the duplicated one.

After traversing all the elements, all the elements in the vector should be negative except the one in the position of the missing value  --- it was never called previously.

## Code

### C++ 

```cpp
class Solution {
public:
    vector<int> findErrorNums(vector<int>& nums) {
        int length = nums.size();
        int i = 0;
        vector<int> res;
        
        for(int i = 0; i < length; i++){
            if (nums[abs(nums[i])-1] < 0) res.push_back(abs(nums[i]));
            else nums[abs(nums[i])-1] = -nums[abs(nums[i])-1];
        }
        
        for(int i = 0; i < length; i++)
            if (nums[i] > 0) res.push_back(i+1);
        
        return res;
    }
};
```

