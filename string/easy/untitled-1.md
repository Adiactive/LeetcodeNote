---
description: 'https://leetcode.com/problems/count-binary-substrings/'
---

# 696. Count Binary Substrings

## Analysis

The number of substrings formed by n continuous 0's and 1's \(vice versa\) is min\(n, m\)

Thus, record the length of previous 0 \(1\) and current 1 \(0\) sequences, when current sequences ends, add min\(preLen, curLen\) to the result, and set the preLen to curLen.

## Code

### C++

```cpp
class Solution {
public:
    int countBinarySubstrings(string s) {
        int size = s.length();
        if (!size) return 1;
        
        int cnt = 0, preLen = 0, curLen = 1;

        for(int i = 1; i < size; i++){
            if (s[i] == s[i-1]){
                curLen++;
            }
            else{
                cnt += min(preLen, curLen);
                preLen = curLen;
                curLen = 1;
            }
        }
        cnt += min(preLen, curLen);
        
        return cnt;
    }
};
```

