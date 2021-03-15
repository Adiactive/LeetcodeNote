# Quick Sort

## Analysis

Line 10 & 13, the operators have to be &gt;= and &lt;= instead of &gt; and &lt;. Or in some cases where left = right, the loop will never stop ---- they keep switching place with each other.

## Code

### C++ 

```cpp
class Solution {
public:
    void quickSort(vector<int>& nums, int left, int right){
        if (left >= right) return;

        int key = nums[left];
        int p = left, q = right;

        while(p < q){
            while(q > p && nums[q] >= key) --q;
            nums[p] = nums[q];

            while(p < q && nums[p] <= key) ++p;
            nums[q] = nums[p];
        }
        nums[p] = key;

        quickSort(nums, left, p-1);
        quickSort(nums, p+1, right);

        return;
    }
    
    vector<int> sortArray(vector<int>& nums) {
        int len = nums.size();
        quickSort(nums, 0, len-1);
        return nums;
    }
};
```

