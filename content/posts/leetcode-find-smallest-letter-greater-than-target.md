---
date: '2026-01-31T09:38:05+08:00'
draft: False
title: 'Leetcode 744 - Find Smallest Letter Greater Than Target'
categories:
- LeetCode
---
## Approach
Binary search on the location of first letter greater than target. (Using built-in upperbound function in C++ is good as well)
## Solution
```cpp
class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        int lo = 0, hi = letters.size() - 1;
        char res = letters[0];
        while (lo <= hi) {
            int mid = (lo + hi) / 2;
            if (letters[mid]-target > 0) res = letters[mid], hi = mid-1;
            else lo = mid+1;
        }
        return res;
    }
};
```
## 心得
之後打算把 **LeetCode 每日問題**的解法丟上來，希望有朝一日能進 Google X)

話說要怎麼幫 github page 設定 custom domain，我想好好利用系上提供的免費的 `csie.org` QQ 但不知道為什麼弄不好，打 A Record 會是爛的，希望改成 CNAME 後 DNS checking 能成功XD


