# Merge Sort

## Analysis

Create temp in advance to avoid repetitive creation in mergeSort\(\)

## Code

### C++ 

```cpp
class Solution {
public:
    void mergeSort(vector<int>& nums, int left, int right, vector<int>& temp){
        if (left + 1 >= right) return;

        int mid = (left + right) / 2;
        mergeSort(nums, 0, mid, temp);
        mergeSort(nums, mid, right, temp);

        int p = left, q = mid, i = left;
        while(p < mid || q < right){
            if (q == right || (p < mid && nums[p] < nums[q])){
                temp[i++] = nums[p++];
            }
            else{
                temp[i++] = nums[q++];
            }
        }

        for (int i = left; i < right; i++){
            nums[i] = temp[i];
        }

        return;
    }
    
    vector<int> sortArray(vector<int>& nums) {
        int len = nums.size();
        vector<int> temp(nums);
        mergeSort(nums, 0, len, temp);
        return nums;
    }
};
```

