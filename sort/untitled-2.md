---
description: 'https://leetcode-cn.com/problems/sort-characters-by-frequency/'
---

# 451. Sort Characters By Frequency

## Analysis

Bucket sort.

## Code

### C++ 

```cpp
class Solution {
public:
    string frequencySort(string s) {
        unordered_map<char,int> map;
        int maxCnt = 0;
        for(const auto& ch : s){
            maxCnt = max(maxCnt, ++map[ch]);
        }

        vector<string> buckets(maxCnt);
        for(const auto& pair : map){
            buckets[pair.second-1] += pair.first;
        }

        string res;
        for(int i = maxCnt - 1; i >= 0; i--){
            for(const auto& ch : buckets[i])
                res += std::string(i+1, ch);
        }

        return res;
    }
};
```

