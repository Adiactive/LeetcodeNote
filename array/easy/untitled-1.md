---
description: 'https://leetcode.com/problems/degree-of-an-array/'
---

# 697. Degree of an Array

## Analysis

Use map to store frequency counts and first/lastIndex. Or, update min length in each iteration and do it in one loop, just a trade-off between time and space.

## Code

### C++ 

```cpp
class Solution {
public:
    int findShortestSubArray(vector<int>& nums) {
        int maxFre = 1;
        int length = nums.size();
        map<int,int> freCnt;
        map<int,int> firstIndex;
        map<int,int> lastIndex;
        
        for(int i = 0; i < length; i++){
            if (freCnt.find(nums[i]) == freCnt.end()){
                freCnt[nums[i]] = 1;
                firstIndex[nums[i]] = i;
                lastIndex[nums[i]] = i;
            }
            else{
                int cnt = ++freCnt[nums[i]];
                maxFre = max(maxFre, cnt);
                lastIndex[nums[i]] = i;
            }
        }
        
        int minLen = length;
        for(auto it = freCnt.begin(); it != freCnt.end(); it++){
            if (it->second == maxFre)
                minLen = min(minLen, lastIndex[it->first] - firstIndex[it->first] + 1);
        }
        
        return minLen;
    }
};
```

