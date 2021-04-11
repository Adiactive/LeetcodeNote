---
description: 'https://leetcode-cn.com/problems/implement-strstr/'
---

# 28. Implement strStr\(\) \(KMP\)

## Analysis

Definitely not an easy question.

## Code

### C++

```cpp
class Solution {
public:
    void buildNext(int *next, const string &needle){
        int len = needle.size(), j = 0;
        next[0] = 0;
        for(int i = 1; i < len; i++){
            while(j && needle[i] != needle[j]) j = next[j-1];
            if(needle[i] == needle[j]) j++;
            next[i] = j;
        }

        return;
    }

    int strStr(string haystack, string needle) {
        int ndlLen = needle.size(), hayLen = haystack.size();
        
        if(!ndlLen) return 0;
        
        int next[ndlLen];
        buildNext(next, needle);
        
        int j = 0;
        for(int i = 0; i < hayLen; i++){
            while(j && haystack[i] != needle[j]) j = next[j-1];
            if(haystack[i] == needle[j]) j++;
            if(j == ndlLen) return i - j + 1;
        }

        return -1;
    }
};
```

