# Quick Sort

## Analysis

Line 10 & 13, the operators have to be >= and <= instead of > and <. Or in some cases where v1=v2.

&#x20;? ? ?  v1   v2  ? ? ?

&#x20;           l     r

the loop will never stop ---- they keep switching place with each other.

Use random pivot to avoid timeout in some special stupid cases.

## Code

### C++&#x20;

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


class Solution {
public:
    void quickSort(vector<int>& nums, int left, int right){
        if (left >= right) return;

        int randIndex = std::rand() % (right - left + 1) + left;
        std::swap(nums[left], nums[randIndex]);
        int key = nums[left];
        int l = left, r = right;
        while(l < r){
            while(l < r && nums[r] >= key) r--;
            while(l < r && nums[l] <= key) l++;

            std::swap(nums[l], nums[r]);
        }
        std::swap(nums[left], nums[l]);
        
        quickSort(nums, left, l-1);
        quickSort(nums, l+1, right);
        return;
    }

    vector<int> sortArray(vector<int>& nums) {
        quickSort(nums, 0, nums.size()-1);
        return nums;
    }
};

```
